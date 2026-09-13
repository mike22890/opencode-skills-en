<!-- 隐式触发：分支管理/分支模型/PR/代码审查/合并/工作流/Git Flow -->
# 分支策略

## 常见模型

### GitHub Flow（简单，推荐）
```
main（永远可发布）
  └── feature/xxx（开发）
        └── PR → review → merge → main
```

### Git Flow（复杂，大团队）
```
main（发布）
develop（集成）
  ├── feature/xxx
  ├── release/x.x
  └── hotfix/xxx
```

### Trunk-Based（高频，CI/CD）
```
main（trunk）
  └── 短命分支（< 1 天）
        └── 直接合并
```

**选择**：小团队 GitHub Flow / 大团队 Git Flow / 成熟 CI Trunk-Based

## 分支命名

```
feature/user-authentication
fix/cart-total-bug
hotfix/security-patch
release/v1.2.0
chore/update-deps
```

**规则**：type/kebab-case-description

## 合并策略

| 策略 | 结果 | 场景 |
|---|---|---|
| Merge commit | 保留全部历史 | 大功能 |
| Squash merge | 一个提交 | 小功能（推荐） |
| Rebase merge | 线性历史 | 个人分支 |

**团队统一**——不要混用。

## PR 规范

### 标题
```
同 commit 规范：feat(scope): description
```

### 描述模板
```markdown
## 做了什么
- 变更点 1
- 变更点 2

## 为什么
[背景/动机]

## 怎么测
- [ ] 单测通过
- [ ] 手动验证 X

## 截图（UI 变更）
[before/after]

## 关联
Closes #123
```

### PR 大小
- **理想**：< 400 行变更
- **可接受**：< 800 行
- **太大**：拆分（reviewer 会恨你）

## Code Review

### 作为作者
- 自审一遍（先自己找问题）
- 写清楚"为什么"
- 小步提交（reviewer 好跟）
- 回应每条评论（改/解释/讨论）

### 作为 reviewer
- 24 小时内回应
- 区分"必须改"和"建议"
- 问问题 > 下命令
- 赞美好的部分

## 速查卡

```
模型：GitHub Flow（简）/ Git Flow（大）/ Trunk（CI）
命名：type/kebab-description
合并：Squash 小功能 / Merge 大功能 / 团队统一
PR：< 400 行 / 标题规范 / 描述含"做了什么+为什么+怎么测"
Review：24h 内 / 必须改 vs 建议
```
