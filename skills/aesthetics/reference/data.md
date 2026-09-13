# Data Viz / Logo / Diagrams

## Data visualization

- **Tufte principle**: maximize data-ink ratio, minimize chartjunk
- Fade gridlines (#E5E5E5 or lighter)
- Colors ≤ 5 (patterns beyond that)
- Label data directly on chart (avoid legends)
- Y-axis starts at 0 (bar charts)
- **Never**: 3D effects / rainbow palettes / pie charts > 5 slices / dual Y-axis / truncated Y-axis / emoji shadows
- **Tools**: D3.js / ECharts / Recharts / Visx / Observable Plot / Vega-Lite
- **Resources**: Information is Beautiful Awards / FlowingData / Observable

## Logo / Brand

- Two versions: monochrome + color
- Three lockups: horizontal + vertical + wordmark
- Minimum recognizable size test (16×16 favicon)
- **Never**: gradients (unless brand needs) / complex illustration (unreadable small) / > 3 colors / ultra-thin type
- **Tools**: Figma / Illustrator / Inkscape / Ideogram / Recraft
- **Resources**: LogoArchive (5000+) / Brand New / LogoMoose

## Flowchart / Architecture diagram

- **Consistent direction** (LR or TD, pick one)
- Nodes ≤ 12 (layer beyond that)
- Color-code: input / process / output
- **Never**: > 20 nodes / chaotic arrows / crossing lines / 3D nodes
- **Tools**: mermaid (recommended) / Graphviz / PlantUML / D2 / Excalidraw

## Dashboard

- **F-pattern reading**: top-left = core KPI, bottom-right = detail
- High density, clear hierarchy
- Numbers get the biggest type
- Chart colors ≤ 3
- Time range / filters fixed at top
- **Never**: 3D pies / rainbow / Y-axis not from 0 / unfixed table columns / colorblind-unfriendly
- **Tools**: shadcn/ui + Recharts / ECharts / D3.js / Tremor / Metabase

## Landing page

- Hero: headline + subhead + CTA + screenshot (not dead-centered)
- One CTA in the primary color
- ≥ 80px whitespace between sections
- Social proof: client logos + numbers + testimonials
- **Never**: filler headlines ("Empower your business") / fake data / > 3 CTAs / > 5 form fields / popup harassment
- **Tools**: shadcn/ui + Next.js / Astro / Framer / Tailwind UI

## Universal carrier self-check

- [ ] Data-ink ratio > 50% (charts)
- [ ] Colorblind-friendly
- [ ] Y-axis from 0
- [ ] Captions + data source
- [ ] Nodes ≤ 12 (diagrams)
- [ ] One hero CTA (landing)
