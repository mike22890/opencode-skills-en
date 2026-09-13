<!-- 隐式触发：配色/字体/设计原则/颜色/字体搭配/视觉规范/设计系统 -->
# 设计原则 / 字体 / 配色（精简）

## 大师学习清单

- **Dieter Rams** —— 诚实克制 / Braun
- **Müller-Brockmann** —— 网格系统
- **Paul Rand** —— Logo 隐喻
- **原研哉** —— "空" / 无印良品
- **Jony Ive** —— 材质 / 苹果早期
- **Edward Tufte** —— 数据墨水比
- **Susan Kare** —— 第一代 Mac 图标

## 字体（4 角色）

| 角色 | 推荐 |
|---|---|
| Display | Geist / IBM Plex Serif / 思源宋体 |
| Body | IBM Plex Sans / Source Sans 3 |
| Mono | JetBrains Mono / Fira Code |
| Accent | IBM Plex Serif / Source Serif |

**禁用默认**：Inter / Roboto / system-ui / Arial / Times / Helvetica（除非致敬）

## 字体配对铁律

1. ≤ 2 家族
2. ≤ 4 字重
3. 一冷一暖
4. 不裸奔默认

## 9 套配色（按情绪）

| 情绪 | 背景 | 主色 | 强调 |
|---|---|---|---|
| 克制理性 | `#F5F4F0` | `#1A1A1A` | `#C8553D` |
| 温暖人文 | `#FAF7F2` | `#3D3935` | `#A85D34` |
| 冷静医疗 | `#F0F4F7` | `#1B2D3F` | `#4A90A4` |
| 古典编辑 | `#F4F1E8` | `#2B2620` | `#7A1F1F` |
| 赛博冷峻 | `#0A0A0A` | `#E8E8E8` | `#5FFF5F` |
| 侘寂东方 | `#EFEBE0` | `#2A2825` | `#8B5A3C` |
| 品牌活力 | `#FFFCF5` | `#0F1419` | `#FF6B35` |
| 深空专业 | `#0E1116` | `#D7DAE0` | `#7C8FFF` |
| 墨韵中文 | `#FAF8F0` | `#1A1815` | `#A03028` |

## 配色禁用

- ❌ Material 紫 `#6750A4`
- ❌ Tailwind 蓝 `#3B82F6` 满铺
- ❌ 彩虹渐变
- ❌ S ≥ 80% 大面积
- ❌ `#000` + `#FFF`（用 `#0A0A0A` + `#FAFAFA`）

## 网格

- 8pt baseline（4/8/16/24/32/48/64/96/128）
- ≤ 4 档间距
- 行高 1.6（body）/ 1.2（heading）/ 1.05（display）
- 字间距 display=-0.02em / body=0 / caption=+0.02em

## 节奏（最重要）

> AI 输出是均匀的，呼吸感来自打破均匀。

- 段落长短句交错（2-3 行 + 1 行 + 5 行）
- 引用独立成段、不缩进、加左边线
- 代码块前后各空 1.5 行
