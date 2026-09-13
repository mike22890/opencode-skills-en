---
name: aesthetics
description: Use for anything "made for human eyes": UI/interfaces/frontend, color, typography, logos, motion, layout, PPT/slides, posters, documents, resumes, charts.
version: 3.0.0
metadata:
  author: mike22890
  tags: ui design aesthetics typography color palette grid master-craft anti-ai material tailwind shadcn print pdf cv resume poster banner social-media ppt slidev typst latex
---

# Aesthetics

## When to trigger (load this skill on sight)

Trigger on any of these keywords: UI, color palette, typography, fonts, PPT, Slidev, shadcn, Material, Antd, Tailwind, logo, icons, motion, shadows, border-radius, whitespace, grid, layout, design, resume, thesis, poster, business card, invitation, social media, Instagram, LinkedIn, email, charts, flowcharts, UX.

## The 6 rules

1. **Typography**: ≤ 2 families / ≤ 4 weights / never ship default Inter/Roboto/system-ui
2. **Color**: HSL workflow / start at saturation ≤ 40% / 60-30-10 / no Material purple
3. **Spacing**: 8pt grid / ≤ 4 spacing steps / rhythm beats symmetry
4. **Hierarchy**: visual hierarchy ≤ 3 levels / focus always visible / motion ≤ 350ms
5. **Anti-AI look**: centered symmetry / even distribution / default fonts / high saturation / rainbow gradients / emoji decoration / card walls — all banned
6. **Self-check**: before shipping, look at it for 5 seconds — would Kenya Hara nod?

## Mandatory self-check

- [ ] Fonts paired, no default fallback
- [ ] Colors muted, accent ≤ 10% of area
- [ ] All spacing multiples of 8
- [ ] Visual hierarchy ≤ 3 levels
- [ ] Focus state visible (a11y, UI only)
- [ ] At least 1-2 breaks in symmetry
- [ ] 5-second look says "premium"

## Loading references (load exactly 1 per task)

`reference/` has 6 files — load by scenario:

| User says | Load |
|---|---|
| Write UI code / frontend / components / dashboard | `reference/ui.md` |
| Pick colors / fonts / design principles | `reference/design.md` |
| Resume / thesis / report / poster / business card / invitation / PPT | `reference/print.md` |
| Instagram / X / LinkedIn / email | `reference/social.md` |
| Charts / flowcharts / logo / data viz / landing page | `reference/data.md` |
| Find master references | `reference/resources.md` |

Universal anti-AI checklist + quick cards → `reference/README.md` (shared by all scenarios)

## Relationship to other skills

- **masterpiece-writing**: text content aesthetics (docs/tutorials/reports)
- **avoid-ai-writing**: removes AI tone from text
- **aesthetics (this skill)**: visual aesthetics (any carrier "made for human eyes")

## Precise triggering

`/design [scenario]` loads the matching scenario template (17 scenarios in command/design.md).
