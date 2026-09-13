<!-- 隐式触发：回退/撤销/恢复/reflog/冲突解决/救援/撤销提交/回滚 -->
# 急救与恢复

## 撤销清单

| 场景 | 命令 |
|---|---|
| 改错最后一个提交信息 | `git commit --amend` |
| 忘记加文件到最后一个提交 | `git add x && git commit --amend --no-edit` |
| 撤销最后一个提交（保留改动） | `git reset --soft HEAD~1` |
| 撤销最后一个提交（丢弃改动） | `git reset --hard HEAD~1` |
| 撤销已推送的提交 | `git revert <hash>`（安全） |
| 撤销工作区改动 | `git restore <file>` |
| 取消暂存 | `git restore --staged <file>` |
| 恢复被删的分支 | `git reflog` + `git checkout -b x <hash>` |

## Reflog（后悔药）

```bash
git reflog
# 找到操作前的 hash
git reset --hard <hash>
```

**Reflog 保留 90 天**（默认）——几乎所有"丢了的"都能找回。

## Revert vs Reset

| | revert | reset |
|---|---|---|
| 原理 | 新提交抵消旧提交 | 移动 HEAD |
| 历史 | 保留（安全） | 改写（危险） |
| 已推送 | ✅ 用 revert | ❌ 不要用 |
| 未推送 | 都行 | 常用 reset |

## 冲突解决

### 步骤
```bash
git status              # 看冲突文件
# 编辑文件（找 <<<<<<< ======= >>>>>>>）
git add <resolved>      # 标记解决
git commit              # 完成合并
```

### 冲突标记
```
<<<<<<< HEAD
你的版本
=======
他们的版本
>>>>>>> branch-name
```

### 策略
- 保留双方（合并逻辑）
- 选一边（明确哪个对）
- 重写（都不对）

### 工具
```bash
git mergetool           # 可视化解决
git checkout --ours x   # 全用我们的
git checkout --theirs x # 全用他们的
```

## 常见急救

### 提交到了错误分支
```bash
git branch correct-branch     # 从当前创建正确分支
git reset --hard HEAD~1       # 当前分支回退
git checkout correct-branch   # 切过去
```

### 想拆开最后一个提交
```bash
git reset HEAD~1              # 撤销提交保留改动
git add -p                    # 分批添加
git commit                    # 分别提交
```

### 误删分支
```bash
git reflog                    # 找分支最后的 hash
git checkout -b <name> <hash> # 恢复
```

### 误 rebase
```bash
git reflog                    # 找 rebase 前的 hash
git reset --hard <hash>
```

### 推送被拒（远程有新提交）
```bash
git pull --rebase             # 拉取并 rebase
git push
# 或者
git pull                      # merge 方式
git push
```

## 危险操作（避免）

```
❌ git push --force            （覆盖远程历史）
❌ git reset --hard            （丢弃未提交改动）
❌ git clean -fd               （删未跟踪文件）
❌ git rebase 已推送的分支     （团队混乱）

✅ git push --force-with-lease （安全强推，检查远程）
✅ 操作前 git status + git stash
✅ 不确定就先备份分支：git branch backup
```

## 速查卡

```
撤销：amend（改提交）/ soft reset（撤提交留改动）/ revert（已推送）
恢复：reflog 万能（90 天）
冲突：edit → add → commit / --ours --theirs
急救：错分支=新分支+reset / 拆提交=reset+add -p / 误删=reflog
危险：force/reset --hard/clean -fd → 先备份分支
```
