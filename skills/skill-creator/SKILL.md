---
name: skill-creator
description: 创建、测试、优化 agent skill。当需要开发新 skill、改进现有 skill、评测 skill 质量、编写 SKILL.md、设计 skill 架构、skill 版本管理、自动化测试、将重复工作流封装为 skill 时使用。也适用于 skill 发布到 GitHub 前的准备工作。
version: 2.0.0
---

# Skill Creator（精简版）

## 何时触发

关键词：创建skill、写skill、开发skill、评测、测试、SKILL.md、架构设计、版本管理、发布skill、打包skill、优化skill、改进skill。

## 核心循环

```
Draft → Test → Evaluate → Improve → Repeat
```

---

## 创建 Skill

### 1. 明确意图

回答这 4 个问题：
1. 这个 skill 让 AI 做什么？
2. 什么时候触发？（用户会怎么说）
3. 输出格式是什么？
4. 需要测试吗？

### 2. 写 SKILL.md

```markdown
---
name: skill-name
description: 简短描述 skill 做什么 + 什么时候触发。要"推一点"（pushy），宁多勿少。
---

# Skill Name

## 何时触发

关键词：xxx/yyy/zzz（口语化，不用正式术语）

## 核心内容

（≤500 行，理想 ≤200）

## 加载 reference（如需要）

| 用户说 | 加载 |
|---|---|
| 关键词A | reference/a.md |
| 关键词B | reference/b.md |
```

### 3. 设计原则

**精简**：SKILL.md ≤500 行，reference 按需加载
**易触发**：description 里塞满触发词，宁多勿少
**分层**：SKILL.md（速查）+ reference/（深挖）
**自动**：用户不用猜关键词，说人话就能命中

---

## 四层路由设计

如果你的 skill 很复杂，用四层路由：

```
第1层：场景感知 → 自动加载基础 skill（如 voice-mastery）
第2层：意图识别 → 映射到技能组（文字/代码/视觉/搜索/安全/...）
第3层：组内匹配 → 所有匹配的都加载，宁多勿少
第3.5层：子 skill 联动 → 读 SKILL.md 加载表 → 自动加载 reference
```

**子 skill 设计**：

```
skill-name/
├── SKILL.md（≤500 行，含加载表）
└── reference/
    ├── topic-a.md（<!-- 隐式触发：关键词1/关键词2 -->）
    └── topic-b.md（<!-- 隐式触发：关键词3/关键词4 -->）
```

**加载表格式**（放在 SKILL.md 里）：

```markdown
## 加载 reference

| 用户说 | 加载 |
|---|---|
| 关键词A/口语1/口语2 | reference/a.md |
| 关键词B/口语3/口语4 | reference/b.md |
```

---

## 触发词设计

### Description 写法

❌ 保守：`"How to build a dashboard"`
✅ 推一点：`"How to build a dashboard. Make sure to use this skill whenever the user mentions dashboards, data visualization, internal metrics, or wants to display any kind of company data, even if they don't explicitly ask for a 'dashboard'."`

### 隐式触发词

每个 reference 文件开头加：
```markdown
<!-- 隐式触发：关键词1/关键词2/关键词3 -->
```

口语化表达（用户实际会说的）：
- ❌ "data visualization" → ✅ "画个图" / "做个图表" / "可视化一下"
- ❌ "refactor code" → ✅ "代码太乱了" / "整理一下" / "重构"

---

## 测试

### 写 2-3 个测试用例

```json
{
  "skill_name": "my-skill",
  "evals": [
    {"id": 1, "prompt": "用户会说的话", "expected_output": "期望结果"},
    {"id": 2, "prompt": "另一种说法", "expected_output": "期望结果"}
  ]
}
```

### 跑测试

- 有 subagent → 并行跑（with-skill vs baseline）
- 没 subagent → 串行跑
- 生成 eval-viewer 给用户看

### 迭代

改到用户满意或反馈为空为止。

---

## 发布前检查

### 安全

- ❌ 不含 malware / 漏洞利用
- ❌ 不含用户隐私数据
- ❌ 不含 API key / token
- ✅ 能在公开 repo 安全发布

### 原创性

- 网上能找到原始出处的 → 删除
- 自己写的 / 大幅修改的 → 保留
- 通用方法论（如 semver、conventional commits）→ 保留（不是别人的）

### 质量

- SKILL.md ≤ 500 行
- 有触发词
- 有 reference 加载表（如有子文件）
- 测试通过

---

## 快速参考

| 操作 | 命令 |
|---|---|
| 创建 skill | 写 SKILL.md + reference/ |
| 测试 | 跑 eval cases → eval-viewer |
| 打包 | `python -m scripts.package_skill <path>` |
| 发布 GitHub | 创建 release + tag |
| 优化触发词 | `python -m scripts.run_loop --eval-set ...` |
