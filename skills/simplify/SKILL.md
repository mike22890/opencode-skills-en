---
name: simplify
description: 代码简化与复杂度降低。当需要重构代码、提升可读性、降低圈复杂度、消除重复、简化逻辑、清理代码、让代码更简洁、更易维护、减少嵌套、提取方法、重命名变量、删除死代码、代码瘦身时使用。
---

# Code Simplification

## 何时触发

关键词命中即触发：简化/降复杂度/消重复/减少嵌套/提取方法/重命名/清理/代码瘦身/可读性。


## Overview

Simplify code by reducing complexity while preserving exact behavior. The goal is not fewer lines - it's code that is easier to read, understand, modify, and debug. Every simplification must pass a simple test: "Would a new team member understand this faster than the original?"

## When to Use

- After a feature is working and tests pass, but the implementation feels heavier than it needs to be
- During code review when readability or complexity issues are flagged
- When you encounter deeply nested logic, long functions, or unclear names
- When refactoring code written under time pressure
- When consolidating related logic scattered across files
- After merging changes that introduced duplication or inconsistency

**When NOT to use:**

- Code is already clean and readable - don't simplify for the sake of it
- You don't understand what the code does yet - comprehend before you simplify
- The code is performance-critical and the "simpler" version would be measurably slower
- You're about to rewrite the module entirely - simplifying throwaway code wastes effort

## The Five Principles

### 1. Preserve Behavior Exactly

Don't change what the code does - only how it expresses it. All inputs, outputs, side effects, error behavior, and edge cases must remain identical. If you're not sure a simplification preserves behavior, don't make it.

Before every change, ask:

- Does this produce the same output for every input?
- Does this maintain the same error behavior?
- Does this preserve the same side effects and ordering?
- What proportionate final-state verification will reveal a behavior change?

### 2. Follow Project Conventions

Simplification means making code more consistent with the codebase, not imposing external preferences.

Before simplifying:

1. Read `AGENTS.md` / project conventions
2. Study how neighboring code handles similar patterns
3. Match the project's style for imports, naming, function style, error handling, and type annotations

Simplification that breaks project consistency is not simplification - it's churn.

### 3. Prefer Clarity Over Cleverness

Explicit code is better than compact code when the compact version requires a mental pause to parse.

- Replace nested ternaries with readable control flow
- Replace dense inline transforms with named intermediate steps when they clarify intent
- Keep helpful names even if they cost a few extra lines

### 4. Maintain Balance

Watch for over-simplification:

- Don't inline away names that carry meaning
- Don't merge unrelated logic into one larger function
- Don't remove abstractions that serve testability or extensibility
- Don't optimize for line count over comprehension

### 5. Scope to What Changed

Default to simplifying recently modified code. Avoid unrelated drive-by refactors unless explicitly asked.

## Process

### Step 1: Understand Before Touching

Before changing or removing anything, understand why it exists.

Answer:

- What is this code's responsibility?
- What calls it? What does it call?
- What are the edge cases and error paths?
- Are there tests that define expected behavior?
- Why might it have been written this way?

If you can't answer these, read more context first.

### Step 2: Look for Simplification Opportunities

Signals:

- Deep nesting
- Long functions with mixed responsibilities
- Nested ternaries
- Boolean flag arguments
- Repeated conditionals
- Generic or misleading names
- Duplicated logic
- Dead code
- Wrappers or abstractions that add no value

### Step 3: Apply Changes Incrementally

Make one simplification at a time.

For each simplification:

1. Make the change
2. Use the proportionate final-state verification plan to check preservation
3. Keep it only when the evidence supports preservation

Separate refactoring from feature work whenever possible.

### Step 4: Verify the Result

After simplifying, confirm:

- The code is genuinely easier to understand
- The diff is clean and reviewable
- Project conventions still match
- No behavior, error handling, or side effects changed

## Guidance for This Repository

- Prefer straightforward TypeScript over clever compression
- Preserve existing runtime behavior, tests, and hooks
- Favor explicit names and smaller focused helpers when they improve readability
- Keep refactors tightly scoped to the task or review feedback

## Final-state verification

Use a proportionate final-state verification plan for the final diff. Run checks
required by repository and release instructions; add or repeat evidence only
when the changed scope or a stated uncertainty warrants it.

---

## 链式触发（与 code-mastery 配合）

本 skill 通常**不独立使用**，必须与 `code-mastery` 链式触发：

```
[1] code-mastery (找标准) → [2] simplify (自动简化) → [4] /code-review (确认)
```

**触发规则**：
- 用户说"简化这段代码" / "清理" / "重写" → 先调 code-mastery 看标准，再调本 skill 自动简化
- 用户说"重构"（语义模糊）→ 优先调 code-mastery + 本 skill（小改动），需要 AST 级重构才调 code-refactor-ast
- `/code-review` 输出"应该改"项时 → 自动用本 skill 处理能自动化的部分

**职责边界**：
- ✅ 本 skill 管：单文件内命名清理、控制流清晰、嵌套变早返回、提取局部函数、删除冗余代码
- ❌ 不管：跨文件重构、AST 变换、架构解耦、提取接口（→ `code-refactor-ast`）

**铁律**：
- ❌ 跳过 code-mastery 直接调本 skill（可能"简化"出违反大师标准的代码）
- ❌ 用本 skill 做行为变更（必须 100% 保留行为）
- ✅ 改动后跑测试 + 调 /code-review 确认

**与其他 skill 协作**：
- 在三件套链中位置：[1] code-mastery → **[2] simplify** → [3] code-refactor-ast → [4] /code-review
- 处理不了的上抛 [3] code-refactor-ast
- 不与 [3] 并行调用（必须先 [2] 再 [3]）
