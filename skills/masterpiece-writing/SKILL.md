---
name: masterpiece-writing
description: 专业文档的排版与内容审美。当需要写 README、设计文档、ADR、技术方案、API 文档、产品文档、报告、白皮书、教程、博客、邮件、任何"给人看"的文字内容时使用。关注结构清晰、排版美观、信息密度、阅读体验、反 AI 味。
version: 1.0.0
metadata:
  author: Mike
  tags: writing aesthetics typography master-craft
---

# Masterpiece Writing

写任何"给人看"的内容时遵循本 skill。**目标**：让读者看不出是 AI 写的。

## 何时使用

写以下内容时**先读本 skill 再动笔**：
- README / 项目文档 / 用户手册
- 设计文档 / ADR / RFC
- 计划 / 报告 / 总结
- 教程 / blog post / 技术文章
- API 文档 / changelog
- 提交信息（精简版）

## 排版铁律（不可破）

### Markdown 结构
- 标题层级 ≤ 3 层（h1/h2/h3，深嵌套用目录代替）
- 段落 ≤ 6 行（重要观点 ≤ 3 行）
- 行宽 ≤ 80 字符（中文 ≤ 50 字/段）
- 段落间空 1 行
- 表格用 markdown 不用长句列表
- 列表 ≤ 5 项（超过就拆或用段落）

### 视觉节奏
- 段落长度必须变化：单句段 + 长段混排
- 单句段落允许（用于强调/转折）
- 列表 vs 段落：枚举用列表，描述用段落
- 引用块 `>` 只用在真正引述（自己观点不要用）
- `---` 分割线用于章节切换，不要滥用

### 字符规范
- 引号 `'` `"` 直引号，不用弯引号 `'` `"`
- 破折号 `--` 或 `—` **每千字最多 1 个**
- Emoji 在 heading **完全禁用**（"## 🚀 What's New" 这种不要）
- Bold 限制：每节 ≤ 1 个 bold 短语（多了反而无强调）
- Sentence case 标题（"What's new" 不是 "What's New"）

## 大师参考（强制至少参考 1 个）

| 大师 | 风格特征 | 在哪里看 |
|---|---|---|
| **Anthony Fu** (antfu) | 行内链接 + emoji 节制 + 短句 + 视觉留白 | antfu.me + github.com/antfu 所有 README |
| **Julia Evans** (b0rk) | 手绘插图 + 口语化 + 节奏跳跃 + 自嘲 | jvns.ca + wizard zines |
| **Stripe API Docs** | 结构化表格 + 极简解释 + 完整示例 | stripe.com/docs/api |
| **Douglas Crockford** | 简洁到骨 + 定义清晰 + 例到位 | crockford.com |
| **Rich Hickey** | 短句 + 对比鲜明 + 不废话 | "Simple Made Easy" 演讲 + 博客 |
| **TJ Holowaychuk** | 直接陈述 + 极简 markdown + 零客套 | tj.github.io + README 范本 |

**写之前**：浏览器打开 1 个大师作品，照着节奏写。

## 反 AI 腔清单（精简版）

完整版见 `avoid-ai-writing` skill。这里只列**常踩**的。

### 必删词（看见就删）
delve / landscape（隐喻）/ tapestry / realm / paradigm / embark / robust / comprehensive / cutting-edge / leverage / pivotal / seamless / meticulously / holistic / actionable / impactful / synergy / beacon / testament / vibrant / bustling

### 必删短语
"Moreover" / "Furthermore" / "In today's [X]" / "It's worth noting that" / "Notably" / "Whether you're [X] or [Y]" / "Let's dive in" / "Imagine a world where" / "marks a pivotal moment" / "the future looks bright" / "only time will tell" / "I hope this helps" / "feel free to reach out"

### 必删结构
- "It's not X, it's Y" / "It's not X. It's Y."（二元对比）
- "X is the language of Y"（强行类比）
- "The catch?" / "Here's the thing" / "Let me be clear"（infomercial 钩子）
- "X is poised to" / "may become one of the most"（模糊预测）
- 5+ 连续 bullet 都是 noun phrase（"Stable mining / Reliable pool / Optimized..."）

## 节奏规则

### 句长搭配
| 句长 | 用途 | 比例 |
|---|---|---|
| ≤ 15 字 | 强调 / 转折 | 30% |
| 15-30 字 | 主体句式 | 50% |
| 30+ 字 | 解释复杂观点 | 20% |

### 段落长度
- 1 句段：强烈观点/转折
- 2-3 句段：常规段落
- 4-6 句段：需要拆
- ≥ 7 句段：**必拆**

### 段落连接
- 不要 "Moreover"/"Furthermore" 开头
- 用连接词（"and"/"but"/"so"/"yet"）或自然过渡
- 段落之间可加 1 句过渡，但不强制

## 写前 5 问

动笔前过这关：

1. **谁读？** 决定技术深度和语气
2. **为什么读？** 决定结构和详略
3. **大师参考？** 至少 1 个，照节奏写
4. **完成定义？** 知道"写完"长什么样
5. **能大声读？** 写完大声读一遍，听起来像人话就发

## 输出示例对比

### ❌ AI 腔
"Welcome to our comprehensive, robust documentation! Whether you're a startup founder or an enterprise architect, our cutting-edge platform empowers you to leverage the power of seamless integration. It's not just a tool — it's a paradigm shift in modern development. Let's dive in!"

### ✅ 大师味（antfu 风格）
"This is a collection of small utilities.

## Install

```bash
pnpm i foo
```

## Why

Three reasons.

1. It's small.
2. It works.
3. The tests pass.

That's it."

## 触发关键词

用户说以下任一即使用本 skill：
- "写 README / 文档 / 设计文档 / ADR / 计划 / 报告"
- "写得漂亮点" / "有审美" / "大师级" / "看起来专业"
- "make this look professional" / "improve the docs" / "polish this"

## 输出后自检

发布前再过一遍：
1. 必删词/短语/结构扫一遍
2. 排版合规（heading/bold/emoji/段落）
3. 大声读一遍
4. 有 AI 味就改到没

**写文档的最高标准**：发出去后，读者不知道是 AI 写的。

## 加载 reference（按需加载）

| 用户说 | 加载 |
|---|---|
| 排版/结构/层级/段落/表格/列表/视觉节奏/格式规范 | 本 skill 正文（排版铁律+节奏规则） |
| AI腔/机器味/去AI/扫腔/人话/口语化/自然 | avoid-ai-writing skill |
| 配色/字体/UI/视觉/设计/美观/界面 | aesthetics skill |
| 参考大师/风格/节奏/简洁/直接 | 本 skill 大师参考表（Anthony Fu / Julia Evans / Stripe 等） |
