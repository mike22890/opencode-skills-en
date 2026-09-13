---
name: code-refactor-ast
description: 基于 AST 的系统化代码重构与架构解耦。当需要大规模重构、拆函数、拆类、提取接口、消除重复代码（DRY）、强制执行单一职责（SRP）、模块拆分、跨文件重构、Drizzle/Prisma 迁移、数据库 schema 变更、向后兼容的代码改动、复杂代码结构改造时使用。
---

# Code Refactoring & Architecture Decoupling

## 何时触发

关键词命中即触发：重构/拆解/拆函数/提取接口/消除重复/DRY/SRP/跨文件/AST/解耦/模块化。


This skill guides structural refactoring while preserving 100% external behavior invariants.

## Core Refactoring Rule: Behavior Invariance
Refactoring MUST NOT change observable behavior. If behavior changes, it is a feature or bugfix, not a refactoring.

---

## 1. Refactoring Workflow Cycle

```
[1. Baseline Tests] -> [2. Identify Smells] -> [3. Atomic Refactor] -> [4. Verify Tests] -> [5. Repeat]
```

1. **Verify Baseline**: Ensure test suite passes 100% before touching code. If tests are missing, write characterization tests first.
2. **Atomic Steps**: Make one structural transformation at a time. Never mix refactoring with business logic changes.
3. **Verify Regression**: Run test suite after every single transformation.
4. **Commit Point**: Commit each clean transformation step with a `refactor(...)` commit.

---

## 2. Common Code Smells & Antidotes

### A. Long Functions / Large Classes (Violation of SRP)
- **Smell**: Functions > 50 lines doing multiple unrelated tasks.
- **Fix**: Extract cohesive logic into pure helper functions or domain service classes. Keep top-level functions as high-level orchestrators.

### B. Duplicate Logic (Violation of DRY)
- **Smell**: Copy-pasted logic across files with minor variations.
- **Fix**: Parameterize differences and extract shared utilities/abstractions.

### C. Deep Nested Conditionals / Arrow Code
- **Smell**: Nested `if/else` ladders > 3 levels deep.
- **Fix**: Use Guard Clauses (early returns), Polymorphism, or Strategy/Lookup tables.

### D. Primitive Obsession & Data Clumps
- **Smell**: Passing 5-8 raw primitive parameters (`string`, `number`, `boolean`) together everywhere.
- **Fix**: Introduce value objects, structured types/interfaces, or parameter objects.

### E. Tight Coupling / Direct Instantiation
- **Smell**: Hardcoded `new ConcreteClass()` inside business logic.
- **Fix**: Invert dependencies (Dependency Injection / Factory / Interface boundary).

---

## 3. TypeScript / JavaScript Specific Best Practices
- Prefer composition over inheritance.
- Prefer immutability (`readonly`, `as const`, pure transforms) over mutable in-place state mutation.
- Use discriminated unions for complex state machine transitions.
- Eliminate `any` casts with precise narrowing / type guards.

---

## 4. 链式触发（与 code-mastery + simplify 配合）

本 skill 是**结构性重构**工具（跨文件、AST 变换、架构解耦），处于代码任务链的**末段**：

```
[1] code-mastery (找标准)
   ↓
[2] simplify (自动简化单文件)
   ↓
[3] code-refactor-ast (本 skill：复杂结构)
   ↓
[4] /code-review (人工审查)
```

**触发规则**：
- 用户说"重构这段" / "拆耦合" / "extract" / "AST" → 先调 code-mastery + simplify，再用本 skill
- simplify 处理不了的（> 50 行函数、跨文件重构、抽象错误、AST 变换）→ 升级到本 skill
- `/code-review` 输出"必须改"项时 → 用本 skill 处理

**职责边界（与 simplify 的区别）**：
- ✅ 本 skill 管：跨文件重构、AST 变换、提取接口/类、架构解耦、DI/Factory 引入
- ❌ 不管：单文件内命名、控制流清晰化、简单提取（→ `simplify`）

**何时升级到本 skill**（simplify 处理的标志）：
- 重构涉及 ≥ 2 个文件
- 需要 AST 级别变换（如批量重命名、签名统一）
- 引入新的接口/抽象层
- 调整依赖方向（DI、Factory）

**铁律**：
- ❌ 跳过 code-mastery / simplify 直接调本 skill
- ❌ 用本 skill 做行为变更（必须 100% 保留行为）
- ❌ 与 simplify 并行调用（必须先 [2] 再 [3]）
- ✅ 每个原子变换后跑测试
- ✅ 重构完调 /code-review 确认

**与其他 skill 协作**：
- 在三件套链中位置：[1] code-mastery → [2] simplify → **[3] code-refactor-ast** → [4] /code-review
- 与 [2] 串联（不并行），是 [2] 升级版
- 完成后必须 [4] 兜底
