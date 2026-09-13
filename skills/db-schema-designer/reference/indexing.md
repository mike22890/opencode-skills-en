<!-- 隐式触发：索引/复合索引/EXPLAIN/查询优化/慢查询/性能调优 -->
# 索引策略

## 索引类型

| 类型 | 结构 | 场景 |
|---|---|---|
| B-Tree | 平衡树 | 默认（=, <, >, BETWEEN, LIKE 'x%'） |
| Hash | 哈希表 | 仅等值查询（=） |
| GIN | 倒排索引 | JSONB / 数组 / 全文搜索 |
| BRIN | 块范围 | 超大表 + 时间序列 |
| 部分索引 | 带 WHERE | 只索引子集（WHERE deleted_at IS NULL） |
| 覆盖索引 | 含列 | 避免回表（INCLUDE） |

## 复合索引（最左前缀）

```sql
CREATE INDEX idx ON orders(user_id, status, created_at);
-- 有效：user_id / user_id+status / user_id+status+created_at
-- 无效：status / created_at / status+created_at
```

**顺序原则**：
1. 等值条件在前
2. 范围条件在后
3. 排序字段最后

## 什么时候加索引

✅ 加：
- WHERE 高频列
- JOIN 外键列
- ORDER BY 列
- 唯一约束列

❌ 不加：
- 小表（< 1000 行）
- 低区分度列（性别/布尔）
- 高频写入列（写放大）
- 从不查询的列

## 索引代价

```
读：加速查询
写：INSERT/UPDATE/DELETE 要维护索引
空间：索引占存储（有时比数据大）
```

**平衡**：OLTP 表索引 ≤ 5-6 个；分析表可以多。

## EXPLAIN 分析

```sql
EXPLAIN ANALYZE SELECT ...;
```

| 信号 | 含义 | 对策 |
|---|---|---|
| Seq Scan（大表） | 全表扫描 | 加索引 |
| Index Scan | 用索引 | ✅ |
| Bitmap Heap Scan | 中等选择性 | 正常 |
| Nested Loop（大表） | 嵌套循环 | 检查索引 |
| Sort（外部） | 磁盘排序 | 加排序索引 |

## 常见问题

### 索引失效
```
❌ WHERE YEAR(created_at) = 2026     -- 函数包裹
✅ WHERE created_at >= '2026-01-01' AND created_at < '2027-01-01'

❌ WHERE name LIKE '%abc'            -- 前置通配
✅ WHERE name LIKE 'abc%'

❌ WHERE status != 'active'          -- 不等于（低效）
✅ 用部分索引
```

### 重复索引
```
idx(a) 和 idx(a, b) —— idx(a) 是冗余的（最左前缀覆盖）
```

### 未使用索引
```sql
-- PostgreSQL
SELECT * FROM pg_stat_user_indexes WHERE idx_scan = 0;
```

## 索引维护

- 定期检查未使用索引（删除）
- 定期 REINDEX（膨胀时）
- 监控索引大小
- 大表加索引用 CONCURRENTLY（不锁表）

## 速查卡

```
类型：B-Tree 默认 / GIN JSON / BRIN 时序 / 部分索引
复合：最左前缀 / 等值前 / 范围后 / 排序最后
加：WHERE/JOIN/ORDER/唯一
不加：小表/低区分/高频写
EXPLAIN：Seq Scan 大表=加索引
```
