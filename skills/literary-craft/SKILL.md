---
name: literary-craft
description: 文学写作的技巧与方法——小说、散文、诗歌、剧本。当需要写故事、小说、短篇、长篇、散文、随笔、评论、诗歌、现代诗、古诗、剧本、台词、人物塑造、情节设计、对话写作、感官描写、意境营造、文学评论、创意写作、内容创作时使用。
version: 2.0.0
metadata:
  author: Mike
  tags: literary fiction writing craft style sensory character plot dialogue rhythm intimacy masters
---

# Literary Craft（文学审美）

## 何时触发

关键词命中即触发：小说/故事/散文/诗歌/剧本/对话/人物/情节/感官/亲密/情欲/禁忌/文风/创意写作。


## 触发
关键词：小说、故事、文章、散文、诗歌、剧本、情书、日记、人物、情节、对话、感官、亲密、情欲、禁忌、文风。

## 信条 6 条

1. **暗示 > 直白** —— show don't tell
2. **感官 > 物理** —— ≥3 感官维度（视/听/嗅/触/味）
3. **情感 > 动作** —— 内在驱动外在
4. **留白 > 堆砌** —— 没说比说的更有力
5. **节奏 > 长度** —— 长短交替，呼吸感
6. **对话 > 叙述** —— 每个角色不同声音（见 `dialogue.md`）

## 强制自检（写完前必过）

- [ ] 感官 ≥ 3 维
- [ ] 暗示 > 直白（不直接说"他悲伤"——让身体说）
- [ ] 节奏有起伏（不单调）
- [ ] 留白用在关键处
- [ ] 对话差异化（去掉名字能分清谁在说）
- [ ] 结尾有力（不烂尾）
- [ ] 读出声像人话

## 加载 reference（按场景只加载 1 个）

| 用户说 | 加载 |
|---|---|
| 学谁像谁 / 文风借鉴 / 大师作品 / 模仿/ 风格参考/ 文学分析 | `reference/masters.md` |
| 写小说 / 故事 / 情节 / 人物 / 剧情设计/ 角色塑造/ 叙事结构/ 冲突 | `reference/techniques.md` |
| 写对话 / 角色声音 / 台词 / 对白/ 人物语言/ 口语化/ 潜台词 | `reference/dialogue.md` |
| 写文章 / 散文 / 随笔 / 评论 / 情书 / 日记 / 读后感/ 日记/ 书信 | `reference/forms.md` |
| 亲密场景 / 情欲描写 / 感官细节 / 禁忌情感 / 床戏/ 欲望/ 身体关系/ 肌肤之亲/ 暗示/ 留白 | `reference/intimacy.md` |
| BDSM / 虐恋 / 暴力 / 公开场合 / 姿势多样性 / 羞辱 / 权力关系/ 支配/ 服从/ 疼痛/ 控制 | `reference/power.md` |

## 与其他 skill 关系

- **masterpiece-writing**：文档审美（实用）
- **literary-craft（本）**：文学审美（艺术）
- **avoid-ai-writing**：AI 腔扫除（通用）
- **aesthetics**：视觉审美

文学性内容通常一起用：masterpiece-writing + literary-craft。

## 触发规则

- 说"写小说/故事/诗" → 自动调本 skill
- 说"写对话/角色声音" → + `dialogue.md`
- 说"亲密/情色/感官" → `intimacy.md`（**专业、克制**）
