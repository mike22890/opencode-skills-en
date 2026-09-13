---
name: code-mastery
description: Use for writing/refactoring/simplifying/optimizing code, naming, comments, error handling. Code aesthetics 5 rules + chain simplify→refactor.
version: 1.0.0
metadata:
  author: mike22890
  tags: code refactor naming function performance style clean-code anti-bloat debug lint format
---

# Code Mastery

## When to trigger (load on sight)

### Writing code (strong trigger)
- Write code / implement feature / write function / method / class / component
- Write API / backend / frontend / CLI / script / tool
- Write SQL / database / ORM
- Write tests / unit tests / integration tests

### Changing code (strong trigger)
- Refactor / simplify / optimize performance / rename / comments
- Add error handling / boundaries / types
- lint / format / prettier / eslint
- debug / fix bug / troubleshoot

### General triggers
- "code quality" / "make it concise" / "don't be verbose" / "performance" / "efficiency"
- "clean code" / "refactor" / "optimize" / "simplify"

## 8 rules (review before writing)

1. **Naming**: narrow / intent-revealing / no abbreviations / no catch-all words / no context repeats
2. **Functions**: ≤ 30 lines (ideally ≤ 10) / 0-2 params / early return / no side effects
3. **Files**: ≤ 200 lines / single responsibility / consistent import order
4. **Comments**: explain "why", not "what" / no restating / delete stale ones
5. **Performance**: O(n) > O(n²) / cache / no allocation in loops / no blocking
6. **Errors**: complete boundaries (null/timeout/exception) / never swallow / carry context
7. **Format**: prettier + 100 col / don't argue style / automate it
8. **Avoid**: over-abstraction / catch-all helpers / 3-layer wrappers / nesting hell / giant files

## Mandatory self-check (before commit)

- [ ] Names reveal intent, no `data/info/item/manager/handler/util/helper`
- [ ] Functions ≤ 30 lines, 0-2 params
- [ ] No 3+ level if nesting (use early returns)
- [ ] Comments explain "why", not restating code
- [ ] No swallowed exceptions (catch must handle or rethrow)
- [ ] No N² loops (unless necessary + commented)
- [ ] No allocation inside loops
- [ ] No catch-all `utils.ts` (split into specific modules)
- [ ] No over-abstraction (Rule of Three: abstract after 3 repeats)
- [ ] Files ≤ 300 lines (split beyond that)
- [ ] 5-second look says "simple"

## After this skill

Load the matching `reference.md` section by scenario:

| User says | Load section |
|---|---|
| Naming / rename | "1. Naming" |
| Functions | "2. Functions" |
| File organization / modules | "3. Files & Modules" |
| Comments | "4. Comments" |
| Performance / optimization | "5. Performance" |
| Error handling / debug | "6. Error Handling" |
| Format / lint | "7. Format" |
| AI code smell / refactor | "8. Anti-AI Code Smell" "9. Refactor Signals" |

## Relationship to other skills

| Skill | Role | Chain position |
|---|---|---|
| **code-mastery (this)** | Master standard / principles | **[1] entry, mandatory** |
| **simplify** | Auto-simplify (within file) | [2] |
| **code-refactor-ast** | AST refactor (cross-file/complex) | [3] |
| **db-schema-designer** | Database schema | Standalone |
| **aesthetics** | Visual aesthetics | Complementary (not same chain) |

## Chain trigger flow (**all code tasks must follow**)

```
[1] code-mastery       ← standards / master taste (this skill, mandatory)
   ↓
[2] simplify           ← what auto-simplify handles (naming, control flow)
   ↓
[3] code-refactor-ast  ← complex structural transforms (split, cross-file, AST)
   ↓
[4] /code-review       ← human confirmation / final check
```

### Trigger rules

| User says | Path |
|---|---|
| Write code / implement / function / class / API | **[1]** |
| Simplify / rewrite / clean up / rename | **[1] + [2]** |
| Refactor / decouple / AST / extract / cross-file | **[1] + [2] + [3]** |
| Code review | **[4]** |
| Any code task **after completion** | Proactively run **[4]** |

### Iron rules

- ❌ Never skip step 1 (never call simplify / code-refactor-ast directly)
- ❌ Never skip levels (code-refactor-ast must pass through simplify first)
- ✅ After any code task, proactively run `/code-review`
- ✅ Fixed order: [1] → [2] → [3] → [4]

## Precise triggers

- "code review" → **[4]** `/code-review` command
- "refactor" → **[1] + [2] + [3]** full chain
- "simplify" → **[1] + [2]**
- "optimize performance" → this skill section 5 + **[4]**
- "debug" / "fix bug" → this skill section 6 + **[4]**
