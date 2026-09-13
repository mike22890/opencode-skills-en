<!-- 隐式触发：命名/函数/文件/注释/性能/错误处理/lint/format/重构/代码质量 -->
# Code Mastery · Reference（精简版）

## 0. 信条

1. 简单 > 复杂
2. 可读 > 聪明
3. 删除 > 添加
4. 直白 > 抽象

**Mike 原话**：补齐边界处理（空/超时/异常），不写裸奔代码。

---

## 1. 命名（最重要）

### 5 原则

1. 窄而意图明确
2. 不缩写（id/url/db/api 除外）
3. 不重复上下文（`user.name` 不 `user.userName`）
4. 避免万能词（data/info/item/manager/handler/util/helper）
5. 同名区分（不要 getX / getXData / getXInfo 三个相似）

### 对比

| ❌ | ✅ |
|---|---|
| `data` | `user`, `orderList`, `config` |
| `temp` | `pendingItems`, `uncommittedBuffer` |
| `processData` | `parseInvoice`, `transformToHtml` |
| `flag` | `isActive`, `shouldRender`, `hasError` |
| `manager` | `cache`, `connectionPool`, `repository` |
| `doStuff` | 描述具体动作 |
| `userInfo` | `user` |
| `string` | `emailAddress`, `displayName` |
| `list` | `pendingOrders` |

### 命名风格

- 变量/函数：camelCase (JS/TS) / snake_case (Python/Go/Rust)
- 类/类型：PascalCase
- 常量：UPPER_SNAKE_CASE
- 文件：kebab-case (web) / snake_case (Python) / PascalCase (React)
- 布尔：`is` / `has` / `should` / `can` 前缀

---

## 2. 函数

### 4 铁律

1. 单一职责
2. ≤ 30 行（理想 ≤ 10）
3. 0-2 参数（3+ 用 options 对象）
4. 无副作用优先（pure > impure）

### 早返回

```ts
// ❌ 深嵌套
if (user) { if (user.isActive) { if (user.hasPermission) { doStuff() }}}

// ✅ 早返回
if (!user) return
if (!user.isActive) return
if (!user.hasPermission) return
doStuff()
```

### 命名 = 动词 + 名词

`parseInvoice` 不是 `invoiceParser` / `fetchUser` 不是 `userFetcher`

---

## 3. 文件 / 模块

- 一个文件 = 一个核心职责，≤ 200 行
- import 顺序：内置 > 第三方 > 本地
- export 在底部集中
- 模块不暴露内部实现、不循环依赖

---

## 4. 注释

### 铁律

1. 解释"为什么"，不是"是什么"
2. 不复述代码
3. 不写"显而易见"的注释
4. 删过时的注释

### 对比

```ts
// ❌ 不好
i++ // i 加 1
fetchUser() // 获取用户
const ratio = 1.250 // 模块化比例

// ✅ 好
// 用 1.250 而不是 1.333 是为了避免视觉跳跃过大
const ratio = 1.250
// throws on 404 by default, see RFC-123
fetchUser(id)
```

---

## 5. 性能 / 省钱

### 算法

- O(n) > O(n²)：用 Set/Map 替代 Array.includes
- O(1) > O(n)：哈希缓存
- 避免深拷贝（结构化克隆 / immutable / 指针共享）

### 常见坑

- ❌ 循环里 new 对象
- ❌ render 函数里 filter/map（用 useMemo）
- ❌ 同步阻塞 IO（用 async/await + Promise.all）
- ❌ 频繁 IO（用 batch + debounce + throttle）
- ❌ 大数组常驻内存（用 stream / cursor / 分页）

### 自检

- [ ] 无 N² 循环（除非必要）
- [ ] 大列表用虚拟滚动
- [ ] 网络请求用缓存（React Query / SWR）
- [ ] 数据库用索引（EXPLAIN 验证）
- [ ] 资源用 CDN + gzip/brotli

### 省钱（Mike 原话）

- **CPU**：算法 + 避免重复计算 + 缓存昂贵操作
- **内存**：避免大对象常驻 + 及时释放 + stream
- **存储**：压缩 + 去重 + 冷热分层
- **网络**：缓存 + 批处理 + gzip + CDN

---

## 6. 错误处理（不写裸奔代码）

### 边界完整

- 空值：`null` / `undefined` / `''` / `[]` / `{}`
- 超时：fetch / DB / user input
- 异常：try / catch 不要吞
- 边界：max / min / length / type mismatch

### 对比

```ts
// ❌ 裸奔
const user = await fetchUser(id)
return user.name

// ✅ 完整
try {
  const user = await fetchUser(id)
  if (!user) throw new NotFoundError(`User ${id}`)
  return user.name
} catch (err) {
  logger.error('fetchUser failed', { id, err })
  throw new UserFetchError(`Failed to fetch user ${id}`, { cause: err })
}
```

### 不要做

- ❌ catch 后什么都不做
- ❌ catch 后只 console.log
- ❌ throw new Error() 不带信息
- ❌ 字符串代替 Error 类型
- ❌ 静默 fail（应该告警）

**黄金法则**：要么处理，要么抛出。

---

## 7. 格式

- 缩进：2 空格 (JS/TS) / 4 空格 (Python)
- 引号：单引号优先
- 行宽 ≤ 100 字符
- 工具强制：Prettier / Black / gofmt / rustfmt / ESLint

---

## 8. 反 AI 代码味 10 条

1. 不写过度抽象（Rule of Three：3 次重复再抽象）
2. 不写万能 helper（拆具体模块）
3. 不写三层 wrapper（至少一层是过度抽象）
4. 不写 `index.ts` 全 re-export（影响 tree-shaking）
5. 不写嵌套 4 层 if（用早返回 / 策略模式）
6. 不写大函数（> 50 行必拆）
7. 不写巨类（> 500 行必拆）
8. 不写巨文件（> 300 行必拆）
9. 不写"看起来很专业"的注释（如 `// init` 在 `init()` 上面）
10. 不写 magic number（用常量命名）

---

## 9. 重构信号

| 信号 | 动作 |
|---|---|
| 同一函数被复制 3 次 | 提取（Rule of Three） |
| 函数 > 50 行 | 拆分 |
| 类 > 500 行 | 拆分 |
| 文件 > 300 行 | 拆分 |
| if 嵌套 > 3 层 | 早返回 |
| 参数 > 3 个 | options 对象 |
| 改 1 个 bug 碰 5 个文件 | 抽象错误（耦合太紧） |
| 万能 `utils.ts` > 200 行 | 拆模块 |
| magic number 出现 3+ 次 | 提常量 |

---

## 10. 速查卡

```
命名  窄 · 意图 · 不缩写 · 不万能词
函数  ≤30 行 · 0-2 参数 · 早返回 · 无副作用
文件  ≤200 行 · 单职责 · import 顺序
注释  解释为什么 · 不复述 · 删过时
性能  O(n) > O(n²) · 缓存 · 不在循环 new
错误  边界完整 · 不吞 · 带信息
格式  prettier · 行宽 100 · 工具强制
避免  过度抽象 · 万能 helper · 嵌套地狱
```

> 好代码是**删出来的**，不是写出来的。5 年后能看懂吗？
