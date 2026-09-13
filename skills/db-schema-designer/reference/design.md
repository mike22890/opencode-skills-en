<!-- 隐式触发：数据库设计/建表/表结构/命名规范/数据类型/规范化 -->
# 数据库设计原则

## 范式速查

| 范式 | 规则 | 场景 |
|---|---|---|
| 1NF | 列原子性（不存逗号分隔） | 总是 |
| 2NF | 非主键列依赖完整主键 | 总是 |
| 3NF | 非主键列不依赖其他非主键 | OLTP 默认 |

**反范式**：读多写少 + 性能瓶颈时，刻意冗余（加冗余列/汇总表）。

## 关系设计

### 一对一
```
users(id, ...) + user_profiles(user_id PK FK, ...)
用：敏感信息分离 / 可选字段多
```

### 一对多
```
orders(user_id FK) → users(id)
FK 加索引（查询必需）
```

### 多对多
```
users + roles + user_roles(user_id, role_id) 联合主键
```

## 命名规范

```
表：复数 snake_case（users / order_items）
列：snake_case（created_at / user_id）
主键：id（或 users_id 表名_主键）
外键：{表名单数}_id（user_id）
时间戳：created_at / updated_at / deleted_at
布尔：is_active / has_paid / can_edit
```

## 常用列模式

```sql
id          BIGINT PRIMARY KEY AUTO_INCREMENT  -- 或 UUID
created_at  TIMESTAMP NOT NULL DEFAULT NOW()
updated_at  TIMESTAMP NOT NULL DEFAULT NOW() ON UPDATE NOW()
deleted_at  TIMESTAMP NULL                     -- 软删除
status      ENUM/VARCHAR + 索引
```

## 软删除 vs 硬删除

| | 软删除 | 硬删除 |
|---|---|---|
| 实现 | deleted_at 时间戳 | DELETE |
| 优点 | 可恢复/审计 | 干净/性能 |
| 缺点 | 查询要过滤/唯一约束麻烦 | 不可恢复 |
| 建议 | 用户数据用软删除 | 日志/临时数据硬删除 |

## 数据类型选择

| 场景 | 选择 |
|---|---|
| 主键 | BIGINT / UUID v7（有序） |
| 金额 | DECIMAL(10,2)（不用 FLOAT） |
| 时间 | TIMESTAMP WITH TIME ZONE |
| 枚举 | VARCHAR + 约束（不用 ENUM——改起来痛） |
| JSON | JSONB（PostgreSQL）/ JSON（MySQL 8+） |
| 短文本 | VARCHAR(n)（按需） |
| 长文本 | TEXT |

## 设计自检

- [ ] 每表有主键？
- [ ] 外键有索引？
- [ ] 金额用 DECIMAL？
- [ ] 时间带时区？
- [ ] 有 created_at / updated_at？
- [ ] 命名一致（全 snake_case）？
- [ ] 没有逗号分隔的多值列？
- [ ] 唯一约束加了吗（email/username）？

## 速查卡

```
范式：3NF 默认 / 读多写少反范式
关系：1-1 分离 / 1-N FK 索引 / N-N 中间表
命名：表复数 / 列 snake / FK {单数}_id
时间戳：created/updated/deleted_at
类型：金额 DECIMAL / 时间带时区 / 主键 BIGINT
```
