---
name: github-workflow
description: GitHub 全流程管理——release、changelog、tag、PR、Actions。当需要管理 GitHub 仓库、创建发布、生成 changelog、打标签、管理 PR、配置 Actions 时使用。安全第一，不泄露隐私，不强制推送。
---

# GitHub Workflow（GitHub 全流程管理）

## 何时触发

关键词命中即触发：GitHub、release、发布、changelog、变更日志、tag、标签、PR、Pull Request、Actions、CI/CD、版本管理、推送代码、创建仓库。

## 铁律（安全第一）

### 绝对禁止

- ❌ `git push --force` / `git push -f`（强制推送）
- ❌ 泄露 token / API key / 私钥
- ❌ 删除远程分支（除非用户明确要求）
- ❌ 直接推送到 main/master（走 PR 流程）
- ❌ 在 commit message 中包含个人信息
- ❌ 创建公开 repo 时包含 .env/密钥文件

### 必须遵守

- ✅ 所有 release 必须对应一个 tag
- ✅ changelog 必须从 commit history 自动生成
- ✅ 版本号遵循 Semantic Versioning（semver）
- ✅ 推送前检查敏感文件（.env, *.pem, *key*）
- ✅ 使用 GitHub Token 进行 API 操作（不暴露给外部）
- ✅ 创建 release 前先检查 tag 是否已存在

---

## 发布流程（Release Workflow）

### 完整步骤

```
1. 检查当前状态
   git status && git log --oneline -10

2. 确定版本号（semver）
   - fix/patch → 1.0.1
   - feat/minor → 1.1.0
   - breaking/major → 2.0.0

3. 生成 CHANGELOG
   - 从上次 tag 到现在的 commit 生成
   - 按 type 分组（Features / Bug Fixes / Breaking Changes）

4. Commit CHANGELOG
   git add CHANGELOG.md
   git commit -m "docs: update changelog for vX.Y.Z"

5. 创建 tag
   git tag -a vX.Y.Z -m "Release vX.Y.Z"

6. Push commits + tags
   git push origin main
   git push origin vX.Y.Z

7. 创建 GitHub Release（API）
   POST /repos/{owner}/{repo}/releases
   {
     "tag_name": "vX.Y.Z",
     "name": "vX.Y.Z",
     "body": "<changelog content>",
     "draft": false,
     "prerelease": false
   }
```

### Changelog 格式

```markdown
# Changelog

## vX.Y.Z - YYYY-MM-DD

### Added（新增）
- 功能描述（commit hash）

### Changed（变更）
- 变更描述

### Fixed（修复）
- Bug 修复描述

### Breaking Changes（破坏性变更）
- 迁移指南
```

### 版本号规则（Semantic Versioning）

| 变更类型 | 版本 bump | 示例 |
|---|---|---|
| Bug fix（patch） | 1.0.0 → 1.0.1 | `fix: resolve login timeout` |
| New feature（minor） | 1.0.0 → 1.1.0 | `feat: add OAuth2 login` |
| Breaking change（major） | 1.0.0 → 2.0.0 | `feat!: change API response format` |

---

## Tag 管理

### 创建 annotated tag
```bash
git tag -a v1.2.3 -m "Release v1.2.3: add user dashboard"
git push origin v1.2.3
```

### 删除本地 tag
```bash
git tag -d v1.2.3
```

### 删除远程 tag（慎用）
```bash
git push --delete origin v1.2.3
```

### 列出所有 tag
```bash
git tag -l --sort=-version:refname
```

### 查看 tag 详情
```bash
git show v1.2.3
```

---

## PR 工作流

### 创建 PR

```bash
# 1. 创建并切换到 feature 分支
git checkout -b feature/my-feature

# 2. 提交更改
git add -A
git commit -m "feat: add new feature"

# 3. 推送分支
git push -u origin feature/my-feature

# 4. 创建 PR（via API）
gh pr create --title "feat: add new feature" --body "Description..."
```

### PR 标题规范（Conventional Commits）

| 前缀 | 用途 |
|---|---|
| `feat:` | 新功能 |
| `fix:` | Bug 修复 |
| `docs:` | 文档变更 |
| `style:` | 代码格式（不影响功能） |
| `refactor:` | 重构 |
| `perf:` | 性能优化 |
| `test:` | 测试 |
| `chore:` | 构建/工具变更 |

### PR 合并

```bash
# Squash merge（推荐，保持 main 干净）
gh pr merge --squash --delete-branch
```

---

## GitHub Actions 基础

### 自动发布 workflow

```yaml
# .github/workflows/release.yml
name: Release
on:
  push:
    tags:
      - 'v*'
jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Create Release
        uses: softprops/action-gh-release@v1
        with:
          generate_release_notes: true
```

---

## 隐私保护检查

### 推送前检查清单

```bash
# 1. 检查是否有敏感文件
git diff --name-only HEAD~1 | grep -E '\.env$|\.pem$|.*key.*|.*secret.*|.*token.*'

# 2. 检查 .gitignore
cat .gitignore | grep -E '\.env|key|pem|secret'

# 3. 检查 commit 中是否有敏感信息
git log -p --all -S 'API_KEY\|TOKEN\|SECRET\|PASSWORD' --source --remotes
```

### 敏感文件模板（.gitgitignore）

```
# 环境变量
.env
.env.local
.env.*.local

# 密钥
*.pem
*.key
*.p12
*.pfx

# 配置文件（含密钥）
config/secrets.yml
credentials.json
```

---

## 常见操作速查

| 操作 | 命令/方法 |
|---|---|
| 创建 release | `POST /repos/{owner}/{repo}/releases` |
| 列出 releases | `GET /repos/{owner}/{repo}/releases` |
| 获取 latest release | `GET /repos/{owner}/{repo}/releases/latest` |
| 创建 tag | `git tag -a vX.Y.Z -m "message"` |
| 删除远程分支 | `git push --delete origin branch-name` |
| 列出所有分支 | `git branch -a` |
| 查看 PR 列表 | `GET /repos/{owner}/{repo}/pulls` |
| 合并 PR | `PUT /repos/{owner}/{repo}/pulls/{number}/merge` |
