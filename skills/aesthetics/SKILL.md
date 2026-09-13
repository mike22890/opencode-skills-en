---
name: aesthetics
description: 视觉审美与设计的综合指南。当任务涉及 UI、界面、前端、配色、字体、Logo、图标、动效、阴影、圆角、留白、间距、网格、排版、PPT、演示文稿、海报、名片、邀请函、简历、毕设、报告、文档、图片、Banner、社交媒体图、数据可视化、信息图表、流程图、品牌设计、网页设计、App 设计、Dashboard、Landing Page、印刷品、任何"给人看"的产出时使用。
version: 3.0.0
metadata:
  author: Mike
  tags: ui design aesthetics typography color palette grid master-craft anti-ai material tailwind shadcn print pdf cv resume poster banner social-media ppt slidev typst latex
---

# Aesthetics

## 何时触发（看到就调本 skill）

关键词命中即触发：UI、配色、字体、PPT、Slidev、shadcn、Material、Antd、Tailwind、Logo、图标、动效、阴影、圆角、留白、网格、排版、设计、简历、毕设、PPT、海报、名片、邀请函、小红书、IG、LinkedIn、邮件、Logo、图表、流程图、UX、好看、丑、美化、高级感、质感。

## 速记 6 条

1. **字体**：≤ 2 家族 / ≤ 4 字重 / 不裸奔 Inter/Roboto/system-ui
2. **配色**：HSL 工作流 / 饱和度 ≤ 40% 起步 / 60-30-10 / 不用 Material 紫
3. **间距**：8pt 网格 / ≤ 4 档间距 / 节奏 > 对称
4. **层级**：视觉层级 ≤ 3 层 / focus 永远可见 / 动效 ≤ 350ms
5. **反 AI 味**：对称居中/平均分布/默认字体/高饱和/彩虹渐变/emoji 装饰/卡片墙 全部禁用
6. **自检**：每次产出前自己看 5 秒 —— 原研哉看到会点头吗？

## 强制自检清单

- [ ] 字体配对且不裸奔默认
- [ ] 配色 muted 起步，强调色 ≤ 10% 面积
- [ ] 间距都是 8 的倍数
- [ ] 视觉层级 ≤ 3 层
- [ ] focus 状态可见（无障碍，仅 UI）
- [ ] 至少 1-2 处打破对称
- [ ] 自己看 5 秒觉得"高级"

## 加载 reference（按场景只加载 1 个）

| 用户说 | 加载 reference 文件 |
|---|---|
| 写代码 UI / 前端 / 组件 / 仪表盘 / 页面/ 网页/ 应用界面/ 组件库 | `reference/ui.md` |
| 选配色 / 字体 / 设计原则 / 颜色/ 字体搭配/ 视觉规范/ 设计系统 | `reference/design.md` |
| 简历 / 毕设 / 报告 / 海报 / 名片 / 邀请函 / PPT / 打印/ 出版物/ 作品 | `reference/print.md` |
| 小红书 / Instagram / X / LinkedIn / 邮件 / 社交媒体/ 配图/ 封面/ 营销图 | `reference/social.md` |
| 图表 / 流程图 / Logo / 数据可视化 / 落地页 / 信息图/ 图标/ 插画 | `reference/data.md` |
| 找大师案例参考 / 灵感/ 参考/ 优秀作品/ 设计趋势 | `reference/resources.md` |

通用反 AI 味 10 条 + 速记卡 → `reference/README.md`（所有场景共享）

## 与其他 skill 的关系

- **masterpiece-writing**：管"文字内容"审美（文档/教程/报告）
- **avoid-ai-writing**：管"文字 AI 腔"扫除
- **aesthetics（本 skill）**：管"视觉"审美（任何"给人看"的载体）

## 精准触发（指定场景）

`/design [场景]` 命令加载对应场景模板（17 个场景在 command/design.md）。
