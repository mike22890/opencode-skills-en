<!-- 隐式触发：UI/前端/组件/仪表盘/页面/网页/应用界面/代码 -->
# UI/前端 参考（精简版）

## 字体 4 角色

| 角色 | 推荐 |
|---|---|
| Display | Geist / IBM Plex Serif / 思源宋体 |
| Body | IBM Plex Sans / Source Sans 3 |
| Mono | JetBrains Mono / Fira Code |
| Accent | IBM Plex Serif / Source Serif |

**铁律**：≤2 家族 / ≤4 字重 / 不裸奔默认

## 5 套组合

| 场景 | Display | Body | Mono |
|---|---|---|---|
| 现代 SaaS | Geist | IBM Plex Sans | JetBrains Mono |
| 温暖人文 | IBM Plex Serif | IBM Plex Sans | JetBrains Mono |
| 东方禅意 | 思源宋体 Heavy | 思源宋体 | JetBrains Mono |
| 赛博未来 | Geist Mono | Geist | Geist Mono |
| 古典编辑 | Playfair Display | Source Serif 4 | JetBrains Mono |

## 配色 HSL

```
主色：H + S≤40% + L40-65% / 背景：S≤10% + L95-98% / 强调：S50-70% + L45-55%
```

**禁用**：Material 紫 / Tailwind 蓝满铺 / 彩虹渐变 / S≥80% 大面积

## 9 套配色

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

## 8pt 网格

间距 4/8/16/24/32/48/64/96/128 / 字号 12/14/16/18/20/24/32/40/56/72+ / 行高 1.6/1.2/1.05

## UI 5 层层级

L1 容器 / L2 表面 / L3 卡片 / L4 浮起 / L5 模态

## 状态反馈

hover/active/focus(2px outline)/disabled(50% opacity) — focus 永远可见

## 动效

150/250/350ms / cubic-bezier(0.4,0,0.2,1) / 只用 opacity/transform/color/shadow

## 圆角

0-2px 工具 / 4-6px 现代 / 8-12px 友好 / 16-24px 圆润 / 999px 胶囊

## 工具

shadcn/ui+Tailwind / Radix UI / Lucide/Phosphor/Tabler

## 自检

focus 可见 / 圆角统一 / 间距 8 倍 / 配色 muted / 移动 375px 不破