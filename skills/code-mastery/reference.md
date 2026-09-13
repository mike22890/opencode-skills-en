# Code Mastery · Reference

## 0. Creed

1. Simple > complex
2. Readable > clever
3. Deleting > adding
4. Direct > abstract

**User's words**: complete the boundaries (null/timeout/exception), never ship naked code.

---

## 1. Naming (most important)

### 5 principles

1. Narrow and intent-revealing
2. No abbreviations (except id/url/db/api)
3. No context repeats (`user.name` not `user.userName`)
4. Avoid catch-all words (data/info/item/manager/handler/util/helper)
5. Distinguish similar names (not getX / getXData / getXInfo)

### Contrasts

| ❌ | ✅ |
|---|---|
| `data` | `user`, `orderList`, `config` |
| `temp` | `pendingItems`, `uncommittedBuffer` |
| `processData` | `parseInvoice`, `transformToHtml` |
| `flag` | `isActive`, `shouldRender`, `hasError` |
| `manager` | `cache`, `connectionPool`, `repository` |
| `doStuff` | describe the specific action |
| `userInfo` | `user` |
| `string` | `emailAddress`, `displayName` |
| `list` | `pendingOrders` |

### Style conventions

- Variables/functions: camelCase (JS/TS) / snake_case (Python/Go/Rust)
- Classes/types: PascalCase
- Constants: UPPER_SNAKE_CASE
- Files: kebab-case (web) / snake_case (Python) / PascalCase (React)
- Booleans: `is` / `has` / `should` / `can` prefix

---

## 2. Functions

### 4 rules

1. Single responsibility
2. ≤ 30 lines (ideally ≤ 10)
3. 0-2 params (3+ → options object)
4. Prefer pure functions

### Early return

```ts
// ❌ deep nesting
if (user) { if (user.isActive) { if (user.hasPermission) { doStuff() }}}

// ✅ early return
if (!user) return
if (!user.isActive) return
if (!user.hasPermission) return
doStuff()
```

### Name = verb + noun

`parseInvoice` not `invoiceParser` / `fetchUser` not `userFetcher`

---

## 3. Files & Modules

- One file = one core responsibility, ≤ 200 lines
- Import order: built-in > third-party > local
- Exports grouped at bottom
- Don't leak internals, no circular deps

---

## 4. Comments

### Rules

1. Explain "why", not "what"
2. Don't restate code
3. No "obvious" comments
4. Delete stale comments

### Contrasts

```ts
// ❌ bad
i++ // increment i
fetchUser() // fetch the user
const ratio = 1.250 // modular scale ratio

// ✅ good
// 1.250 instead of 1.333 to avoid too-large visual jumps
const ratio = 1.250
// throws on 404 by default, see RFC-123
fetchUser(id)
```

---

## 5. Performance

### Algorithms

- O(n) > O(n²): Set/Map instead of Array.includes
- O(1) > O(n): hash caching
- Avoid deep copies (structured clone / immutable / shared pointers)

### Common traps

- ❌ Allocation inside loops
- ❌ filter/map in render (use useMemo)
- ❌ Synchronous blocking IO (async/await + Promise.all)
- ❌ Frequent IO (batch + debounce + throttle)
- ❌ Large arrays resident in memory (stream / cursor / pagination)

### Self-check

- [ ] No N² loops (unless necessary)
- [ ] Large lists use virtual scrolling
- [ ] Network requests cached (React Query / SWR)
- [ ] DB indexes (verified with EXPLAIN)
- [ ] Assets on CDN + gzip/brotli

### Cost discipline

- **CPU**: algorithms + avoid recompute + cache expensive ops
- **Memory**: no resident large objects + release promptly + stream
- **Storage**: compress + dedupe + hot/cold tiering
- **Network**: cache + batch + gzip + CDN

---

## 6. Error Handling (no naked code)

### Complete boundaries

- Nulls: `null` / `undefined` / `''` / `[]` / `{}`
- Timeouts: fetch / DB / user input
- Exceptions: try/catch, never swallow
- Bounds: max / min / length / type mismatch

### Contrasts

```ts
// ❌ naked
const user = await fetchUser(id)
return user.name

// ✅ complete
try {
  const user = await fetchUser(id)
  if (!user) throw new NotFoundError(`User ${id}`)
  return user.name
} catch (err) {
  logger.error('fetchUser failed', { id, err })
  throw new UserFetchError(`Failed to fetch user ${id}`, { cause: err })
}
```

### Never

- ❌ Empty catch blocks
- ❌ catch that only console.logs
- ❌ `throw new Error()` without context
- ❌ Strings instead of Error types
- ❌ Silent failures (should alert)

**Golden rule**: handle it or throw it.

---

## 7. Format

- Indent: 2 spaces (JS/TS) / 4 spaces (Python)
- Quotes: single preferred
- Line width ≤ 100 chars
- Enforce with tools: Prettier / Black / gofmt / rustfmt / ESLint

---

## 8. Anti-AI Code Smell (10 rules)

1. No over-abstraction (Rule of Three: abstract after 3 repeats)
2. No catch-all helpers (split into specific modules)
3. No 3-layer wrappers (at least one is over-abstraction)
4. No re-export-everything `index.ts` (breaks tree-shaking)
5. No 4-level nested if (early return / strategy pattern)
6. No large functions (> 50 lines must split)
7. No giant classes (> 500 lines must split)
8. No giant files (> 300 lines must split)
9. No "looks professional" comments (`// init` above `init()`)
10. No magic numbers (name them as constants)

---

## 9. Refactor Signals

| Signal | Action |
|---|---|
| Same function copied 3 times | Extract (Rule of Three) |
| Function > 50 lines | Split |
| Class > 500 lines | Split |
| File > 300 lines | Split |
| if nesting > 3 levels | Early return |
| Params > 3 | Options object |
| Fix 1 bug touches 5 files | Wrong abstraction (too coupled) |
| Catch-all `utils.ts` > 200 lines | Split into modules |
| Magic number appears 3+ times | Extract constant |

---

## 10. Quick card

```
Naming: narrow · intent · no abbrev · no catch-all
Functions: ≤30 lines · 0-2 params · early return · no side effects
Files: ≤200 lines · single duty · import order
Comments: why not what · no restating · delete stale
Performance: O(n) > O(n²) · cache · no allocation in loops
Errors: complete boundaries · never swallow · carry context
Format: prettier · 100 cols · enforced
Avoid: over-abstraction · catch-all helpers · nesting hell
```

> Good code is **deleted into existence**, not written. Will it be readable in 5 years?
