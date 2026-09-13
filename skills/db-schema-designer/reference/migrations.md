<!-- 隐式触发：迁移/零停机/回滚/大表/生产环境/安全变更/在线迁移 -->
# 迁移安全

## 迁移原则

```
1. 可逆（有 up 和 down）
2. 小步（一次一个变更）
3. 不破坏（向后兼容）
4. 可回滚（数据不丢）
5. 先测试（staging 验证）
```

## 危险操作清单

| 操作 | 风险 | 安全做法 |
|---|---|---|
| DROP COLUMN | 数据丢失 | 先标记废弃→双写→再删（3 步） |
| RENAME COLUMN | 代码全挂 | 加新列→双写→迁移→删旧列 |
| 改类型 | 锁表+数据丢失 | 新列+迁移+切换 |
| 加 NOT NULL | 旧数据违约 | 先填默认值→再加约束 |
| 加索引 | 锁表（大表） | CONCURRENTLY |
| 大表 UPDATE | 锁+长事务 | 分批（每批 1000 行） |

## 扩展-收缩模式（零停机）

```
扩展阶段：
1. 加新列（nullable）
2. 代码双写（旧+新）
3. 回填数据（分批）
4. 代码读新列

收缩阶段：
5. 停止写旧列
6. 删除旧列
```

**每步都可回滚**——这就是安全的核心。

## 迁移文件规范

```
migrations/
├── 20260101_120000_create_users.sql
├── 20260102_090000_add_email_index.sql
└── 20260103_140000_add_status_column.sql
```

**命名**：时间戳 + 动作描述（snake_case）

**内容**：
```sql
-- Up
ALTER TABLE users ADD COLUMN status VARCHAR(20);

-- Down
ALTER TABLE users DROP COLUMN status;
```

## 工具对比

| 工具 | 特点 |
|---|---|
| Prisma Migrate | TypeScript 生态 / 自动生成 |
| Drizzle Kit | 轻量 / SQL-first |
| Flyway | Java / SQL 文件 |
| Liquibase | XML/YAML/SQL |
| Alembic | Python / SQLAlchemy |
| golang-migrate | Go / 简单 |

## 部署流程

```
1. 写迁移（up + down）
2. 本地测试（up → down → up）
3. Staging 验证（真实数据量）
4. 备份生产（必做）
5. 部署迁移（监控）
6. 验证（查询 + 应用）
7. 观察期（1-2 天再删旧结构）
```

## 回滚决策

| 情况 | 动作 |
|---|---|
| 迁移失败 | 立即 down |
| 迁移成功但应用报错 | 修复应用（不回滚） |
| 性能劣化 | 评估（加索引/优化） |
| 数据损坏 | 从备份恢复 |

## 大表迁移技巧

```sql
-- 分批更新（避免长事务）
UPDATE users SET status = 'active' 
WHERE id IN (SELECT id FROM users WHERE status IS NULL LIMIT 1000);
-- 重复直到完成
```

```sql
-- 并发加索引（PostgreSQL）
CREATE INDEX CONCURRENTLY idx_users_status ON users(status);
```

## 速查卡

```
原则：可逆/小步/兼容/可回滚/先测试
危险：DROP/RENAME/改类型/加 NOT NULL → 用扩展-收缩
零停机：加新列→双写→回填→切读→停写→删旧
大表：分批 1000 行 / CONCURRENTLY
流程：写→测→staging→备份→部署→验证→观察
```
