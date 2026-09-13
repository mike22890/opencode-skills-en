---
name: db-schema-designer
description: 数据库 schema 设计、ORM 建模与迁移安全。当需要设计数据库表结构、写 ORM schema（Prisma/Drizzle/TypeORM/Sequelize）、数据库迁移、索引优化、关系设计（1-1/1-N/N-N）、PostgreSQL/MySQL/SQLite/MongoDB 选型、数据库规范化、反范式设计、查询性能优化时使用。
---

# Database Schema & Migration Engineering Guide

This skill provides expert design patterns for relational data modeling, indexing strategies, and zero-downtime migrations.

## 何时触发

关键词命中即触发：数据库、建表、表结构、schema、ORM、Prisma、Drizzle、迁移、索引、关系、外键、PostgreSQL、MySQL、MongoDB、SQL、查询优化、性能、规范化。

---

## 1. Schema Design Standards

### Primary Keys
- Distributed / Microservices: Prefer `UUIDv7` (time-ordered, index-friendly) or `ULID`.
- Single-instance SQL: `BIGINT GENERATED ALWAYS AS IDENTITY` (PostgreSQL) or `AUTO_INCREMENT` (MySQL).

### Timestamps & Audit Fields
- Always include:
  - `created_at TIMESTAMPTZ NOT NULL DEFAULT CURRENT_TIMESTAMP`
  - `updated_at TIMESTAMPTZ NOT NULL DEFAULT CURRENT_TIMESTAMP`
  - `deleted_at TIMESTAMPTZ NULL` (if soft deletes are required)

### Foreign Keys & Integrity
- Always define foreign keys with explicit `ON DELETE` behavior (`CASCADE`, `SET NULL`, or `RESTRICT`).
- ALWAYS index foreign key columns to prevent table locks and slow joins.

---

## 2. Indexing Strategy & Optimization

1. **Composite Index Column Order (Equality First, Range Last)**:
   - Rule: Place columns filtered by exact equality (`=`) first, followed by columns used in ranges (`>`, `<`, `BETWEEN`) or `ORDER BY`.
2. **Covering Indexes (Index-Only Scans)**:
   - Include frequently selected columns in `INCLUDE (...)` clause to avoid heap fetches.
3. **Partial / Filtered Indexes**:
   - For soft-deleted tables: `CREATE INDEX idx_active_users ON users (email) WHERE deleted_at IS NULL;`
4. **Avoid Over-Indexing**:
   - Each index adds write overhead (INSERT/UPDATE/DELETE). Prune redundant or prefix-overlapping indexes.

---

## 3. Zero-Downtime Migration Safety Checklist

When modifying production schemas:
- **Never rename or drop a column in one step**:
   1. Add the new column (nullable or with default).
   2. Dual-write in application code (write to both old and new columns).
   3. Backfill existing historical rows.
   4. Switch reads to the new column.
   5. Remove old column references from code.
   6. Drop the old column in a later release.
- **PostgreSQL Concurrent Indexes**:
   - Use `CREATE INDEX CONCURRENTLY` to avoid taking an exclusive table lock.
- **Adding NOT NULL constraints**:
   - Add column as `NULL`, backfill defaults, add check constraint `NOT VALID`, then `VALIDATE CONSTRAINT`.
- **Set lock timeouts**:
   - Always set `SET lock_timeout = '2s';` before running risky DDL.

---

## 加载 reference

| 用户说 | 加载 |
|---|---|
| 数据库设计 / 建表 / 表结构 / 命名规范 / 数据类型 / 规范化/ 范式 | `reference/design.md` |
| 索引 / 复合索引 / EXPLAIN / 查询优化 / 慢查询/ 性能调优/ 覆盖索引 | `reference/indexing.md` |
| 迁移 / 零停机 / 回滚 / 大表/ 生产环境/ 安全变更/ 在线迁移 | `reference/migrations.md` |
