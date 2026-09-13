---
name: git-workflow
description: Git 工作流的自动化与最佳实践。当需要写 commit message、创建 PR、解决合并冲突、分支管理（Git Flow/GitHub Flow/Trunk-based）、git rebase、cherry-pick、tag 管理、版本发布、git hook 配置、多分支协作、代码审查流程时使用。
---

# Git Workflow & Release Guidelines

This skill guides atomic, safe, and standardized Git version control workflows.

## 何时触发

关键词命中即触发：git、commit、PR、MR、分支、合并、冲突、rebase、cherry-pick、tag、发布、hook、协作、代码审查、回退、撤销、版本管理。

## 1. Pre-Commit Verification Checklist

Before staging or committing any changes:
1. **Check Status & Diffs**:
   - Run `git status -s` to inspect untracked and modified files.
   - Run `git diff` (and `git diff --cached`) to verify exact changes line-by-line.
2. **Security & Secret Screening**:
   - NEVER commit `.env`, `.pem`, credentials, API tokens, or hardcoded secrets.
   - Ensure build artifacts (`node_modules/`, `dist/`, `.turbo/`, `target/`) are ignored via `.gitignore`.
3. **Verification**:
   - Ensure linter and tests pass before committing (`npm test`, `cargo test`, `pytest`, etc.).

---

## 2. Conventional Commit Standards

Follow the Conventional Commits format:
```
<type>(<optional scope>): <short summary in imperative present tense>

[optional body explaining WHY and WHAT changed, not HOW]

[optional footer(s), e.g., BREAKING CHANGE: ..., Closes #123]
```

### Commit Types:
- `feat`: A new user-facing feature or capability
- `fix`: A bug fix
- `refactor`: Code change that neither fixes a bug nor adds a feature
- `perf`: Performance improvements
- `test`: Adding or correcting tests
- `docs`: Documentation changes only
- `chore`: Build system, CI/CD, dependency updates, internal tooling
- `style`: Formatting, whitespace (no code behavior change)

### Good Examples:
- `feat(auth): add OAuth2 refresh token rotation mechanism`
- `fix(parser): handle empty markdown frontmatter without crashing`
- `refactor(db): extract connection pool singleton to separate module`

---

## 3. Pull Request (PR) Preparation

When preparing a PR:
1. **Title**: Concise Conventional Commit style summary.
2. **Summary of Changes**: Bullet points of key architectural/logic modifications.
3. **Testing Plan**: Exact commands executed and tests verified.
4. **Breaking Changes & Risk Assessment**: Detail any backward-incompatible changes or deployment risks.

---

## 4. Conflict Resolution Protocol

1. Run `git status` to identify all unmerged paths.
2. Open conflicting files, locate `<<<<<<<`, `=======`, and `>>>>>>>` markers.
3. Understand the intent of both branches before resolving.
4. Keep the correct logic, remove conflict markers, and run the test suite to verify zero regressions.

---

## 加载 reference

| 用户说 | 加载 |
|---|---|
| commit message / 提交信息/ 提交规范/ 怎么写commit/ 提交格式 | `reference/commits.md` |
| 分支管理 / 分支模型 / PR / 代码审查 / 合并/ 工作流/ Git Flow | `reference/branching.md` |
| 回退 / 撤销 / 恢复 / reflog / 冲突解决 / 救援/ 撤销提交/ 回滚 | `reference/recovery.md` |
