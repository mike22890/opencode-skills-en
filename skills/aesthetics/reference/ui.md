# UI / Frontend Reference

## Typography 4 roles

| Role | Recommendations |
|---|---|
| Display | Geist / IBM Plex Serif / Source Han Serif |
| Body | IBM Plex Sans / Source Sans 3 |
| Mono | JetBrains Mono / Fira Code |
| Accent | IBM Plex Serif / Source Serif |

**Rule**: ≤ 2 families / ≤ 4 weights / no defaults

## 5 pairings

| Scenario | Display | Body | Mono |
|---|---|---|---|
| Modern SaaS | Geist | IBM Plex Sans | JetBrains Mono |
| Warm humanist | IBM Plex Serif | IBM Plex Sans | JetBrains Mono |
| Eastern zen | Source Han Serif Heavy | Source Han Serif | JetBrains Mono |
| Cyber future | Geist Mono | Geist | Geist Mono |
| Classical editorial | Playfair Display | Source Serif 4 | JetBrains Mono |

## Color in HSL

```
Primary: H + S≤40% + L40-65% / Background: S≤10% + L95-98% / Accent: S50-70% + L45-55%
```

**Banned**: Material purple / Tailwind blue full-bleed / rainbow gradients / S≥80% large areas

## 9 palettes

| Mood | Background | Primary | Accent |
|---|---|---|---|
| Restrained | `#F5F4F0` | `#1A1A1A` | `#C8553D` |
| Warm | `#FAF7F2` | `#3D3935` | `#A85D34` |
| Calm | `#F0F4F7` | `#1B2D3F` | `#4A90A4` |
| Classical | `#F4F1E8` | `#2B2620` | `#7A1F1F` |
| Cyber | `#0A0A0A` | `#E8E8E8` | `#5FFF5F` |
| Wabi-sabi | `#EFEBE0` | `#2A2825` | `#8B5A3C` |
| Vibrant | `#FFFCF5` | `#0F1419` | `#FF6B35` |
| Deep space | `#0E1116` | `#D7DAE0` | `#7C8FFF` |
| Ink | `#FAF8F0` | `#1A1815` | `#A03028` |

## 8pt grid

Spacing 4/8/16/24/32/48/64/96/128 / Sizes 12/14/16/18/20/24/32/40/56/72+ / Line-height 1.6/1.2/1.05

## UI 5-level elevation

L1 container / L2 surface / L3 card / L4 raised / L5 modal

## State feedback

hover/active/focus(2px outline)/disabled(50% opacity) — focus always visible

## Motion

150/250/350ms / cubic-bezier(0.4,0,0.2,1) / only opacity/transform/color/shadow

## Border radius

0-2px tools / 4-6px modern / 8-12px friendly / 16-24px soft / 999px pill

## Tools

shadcn/ui+Tailwind / Radix UI / Lucide/Phosphor/Tabler

## Self-check

focus visible / radius consistent / spacing multiples of 8 / muted colors / mobile 375px unbroken
