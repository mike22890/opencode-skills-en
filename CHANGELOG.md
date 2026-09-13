# Changelog

## v2.0.0 - 2026-09-14

### 重大变更

- **四层路由系统** — 从"单 skill 匹配"升级为四层自动路由：
  - 第1层：场景感知（聊天/角色扮演自动加载 voice-mastery）
  - 第2层：意图识别（11 个意图组）
  - 第3层：组内精确匹配（宁多勿少，不设上限）
  - 第3.5层：子 skill 联动（自动加载 reference 文件）

- **隐式触发词** — 每个 skill 和 reference 文件都加了口语化触发词
  - 主 skill：description 追加隐式触发（如 "太乱了"、"不好看"、"帮我选"）
  - Reference 文件：`<!-- 隐式触发：... -->` 标签
  - 不再需要猜关键词，说人话就能命中

- **子 skill 联动** — 加载主 skill 后自动读 SKILL.md 的 reference 加载表，按需加载子文件
  - 例如："写小说里的亲密对话" → literary-craft + techniques.md + dialogue.md + intimacy.md
  - 一个任务可触发多个 reference，自动组合

- **加载表格式统一** — 所有 reference 加载表统一为表格格式：`| 用户说 | 加载 |`
  - 27 个 skill 有 reference 加载表
  - 覆盖所有子文件的路由规则

### 新增 Skill（26 个）

- applying-ui-design-system — 设计系统选型/实现
- avoid-ai-writing — AI 腔扫除
- clonedeps — 克隆依赖源码阅读
- code-refactor-ast — AST 大规模重构
- codemap — 代码地图/新人 onboarding
- codeql — CodeQL SAST 扫描
- copywriting — 营销文案
- cro — 转化率优化
- db-schema-designer — 数据库 schema 设计
- differential-review — 安全 Diff 审查
- fp-check — 漏洞验证/误报消除
- frontend-design — 前端视觉设计
- git-workflow — Git 工作流
- marketing-psychology — 营销心理学
- mcp-builder — MCP 服务器开发
- orchestrating-adversarial-reviews — 多 agent 对抗审查
- pandoc — 文档格式转换
- pptx — PPT 制作
- pricing — 定价策略
- property-based-testing — 属性测试/模糊测试
- sarif-parsing — SARIF 解析
- semgrep — Semgrep 扫描
- sharp-edges — 危险 API 识别
- simplify — 代码简化
- skill-creator — Skill 开发
- supply-chain-risk-auditor — 供应链审计
- variant-analysis — 漏洞变体挖掘
- worktrees — Git Worktree 管理

### 移除 Skill（2 个）

- psychology-mastery — 隐私考虑，不公开发布
- literary-craft — 成人内容，不公开发布

### 旧版对比

| | v1.x | v2.0 |
|---|---|---|
| 触发方式 | 关键词硬匹配 | 四层路由 + 隐式触发 |
| 子 skill | 不自动加载 | 自动加载 reference |
| 加载数量 | 限制 2-4 个 | 宁多勿少，不设上限 |
| Reference 支持 | 仅主 skill | 61 个 reference 文件 + 触发标签 |
| Skill 数量 | 15 | 41 |
