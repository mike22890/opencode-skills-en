<!-- 隐式触发：commit message/提交信息/提交规范/怎么写commit/提交格式 -->
# 提交规范

## Conventional Commits

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Type 清单

| Type | 用途 |
|---|---|
| feat | 新功能 |
| fix | 修 bug |
| docs | 文档 |
| style | 格式（不影响代码） |
| refactor | 重构（不是 feat/fix） |
| perf | 性能优化 |
| test | 测试 |
| build | 构建/依赖 |
| ci | CI 配置 |
| chore | 杂务 |
| revert | 回滚 |

### 示例

```
feat(auth): add JWT refresh token

- Add /refresh endpoint
- Store refresh tokens in Redis with 7d TTL
- Invalidate on logout

Closes #123
```

```
fix(cart): correct total when discount applied

The discount was applied before tax, causing wrong totals.

Fixes #456
```

## Subject 写法

- **动词开头**（add/fix/update/remove/refactor）
- **小写**（除非专有名词）
- **无句号**
- **≤ 50 字符**
- **说"做了什么"**（不是"改了什么文件"）

```
❌ update code
❌ fixed bug
❌ 修改了一些东西
✅ fix null pointer in user parser
✅ add rate limiting to login endpoint
```

## 提交拆分

### 一个提交 = 一件事

```
✅ 拆开：
- feat: add search endpoint
- test: add search endpoint tests
- docs: document search API

❌ 合在一起：
- feat: add search + tests + docs + fix typo
```

### 拆的判断
- 能独立回滚吗？
- 能独立描述吗？
- 是一个逻辑变更吗？

## Body 写法

- 为什么 > 是什么（代码已经说了是什么）
- 解释背景/权衡/副作用
- 用 bullet 列要点
- 每行 ≤ 72 字符

## Footer

```
Closes #123        -- 关闭 issue
Fixes #456         -- 修复 issue
BREAKING CHANGE:   -- 破坏性变更（必写）
Co-authored-by:    -- 协作
```

## 好提交 vs 坏提交

```
❌ 坏：
"fix stuff"
"WIP"
"asdf"
"update"

✅ 好：
"fix: prevent race condition in order creation"
"perf: cache user lookups with 5min TTL"
"refactor: extract payment validation to service"
```

## 速查卡

```
格式：type(scope): subject
Type：feat/fix/docs/refactor/perf/test/chore
Subject：动词开头/小写/≤50/无句号
拆分：一个提交一件事
Body：为什么 > 是什么
Footer：Closes/Fixes/BREAKING CHANGE
```
