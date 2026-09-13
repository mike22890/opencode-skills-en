# Design Principles / Typography / Color

## Masters to learn from

- **Dieter Rams** — honest restraint / Braun
- **Müller-Brockmann** — grid systems
- **Paul Rand** — logo metaphor
- **Kenya Hara** — "emptiness" / Muji
- **Jony Ive** — materials / early Apple
- **Edward Tufte** — data-ink ratio
- **Susan Kare** — first-gen Mac icons

## Typography (4 roles)

| Role | Recommendations |
|---|---|
| Display | Geist / IBM Plex Serif / Source Han Serif |
| Body | IBM Plex Sans / Source Sans 3 |
| Mono | JetBrains Mono / Fira Code |
| Accent | IBM Plex Serif / Source Serif |

**Banned defaults**: Inter / Roboto / system-ui / Arial / Times / Helvetica (unless as homage)

## Font pairing rules

1. ≤ 2 families
2. ≤ 4 weights
3. One warm, one cool
4. Never ship defaults

## 9 palettes (by mood)

| Mood | Background | Primary | Accent |
|---|---|---|---|
| Restrained rational | `#F5F4F0` | `#1A1A1A` | `#C8553D` |
| Warm humanist | `#FAF7F2` | `#3D3935` | `#A85D34` |
| Calm medical | `#F0F4F7` | `#1B2D3F` | `#4A90A4` |
| Classical editorial | `#F4F1E8` | `#2B2620` | `#7A1F1F` |
| Cyber cold | `#0A0A0A` | `#E8E8E8` | `#5FFF5F` |
| Wabi-sabi East | `#EFEBE0` | `#2A2825` | `#8B5A3C` |
| Brand vibrant | `#FFFCF5` | `#0F1419` | `#FF6B35` |
| Deep-space pro | `#0E1116` | `#D7DAE0` | `#7C8FFF` |
| Ink Chinese | `#FAF8F0` | `#1A1815` | `#A03028` |

## Banned colors

- ❌ Material purple `#6750A4`
- ❌ Tailwind blue `#3B82F6` full-bleed
- ❌ Rainbow gradients
- ❌ S ≥ 80% over large areas
- ❌ Pure `#000` + `#FFF` (use `#0A0A0A` + `#FAFAFA`)

## Grid

- 8pt baseline (4/8/16/24/32/48/64/96/128)
- ≤ 4 spacing steps
- Line-height 1.6 (body) / 1.2 (heading) / 1.05 (display)
- Letter-spacing display=-0.02em / body=0 / caption=+0.02em

## Rhythm (most important)

> AI output is uniform. Breathing comes from breaking uniformity.

- Alternate paragraph lengths (2-3 lines + 1 line + 5 lines)
- Quotes standalone, no indent, left rule
- 1.5 lines of air around code blocks
