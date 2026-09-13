# OpenCode Skills EN

![GitHub stars](https://img.shields.io/github/stars/mike22890/opencode-skills-en?style=social)
![License](https://img.shields.io/github/license/mike22890/opencode-skills-en)
![Skills](https://img.shields.io/badge/skills-40-blue)
![Version](https://img.shields.io/badge/version-v4.0.0-green)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen)

> English-first AI Agent Skills collection — 40 original domain methodologies, 4-layer auto-routing, colloquial triggers, no keyword guessing needed.

A collection of 40 original agent skills for [OpenCode](https://opencode.ai), [Claude Code](https://claude.ai/code), [Codex CLI](https://github.com/openai/codex), and any agent that supports the [Agent Skills](https://agentskills.io) standard.

---

## Why This Set

Most English skills trigger on formal keywords — say "write a doc" and they wake up; say "搞个文档" and they stare at you blankly.

This set is different:

- **Colloquial triggers** — natural language just works, no keyword guessing
- **4-layer routing** → scene → intent → group match → sub-skill chaining
- **Implicit triggers** — every skill and reference has colloquial trigger words
- **40 original skills** — all self-written, no public duplicates

---

## 4-Layer Routing

```
Layer 1: Scene awareness → auto-loads voice-mastery for chat/roleplay
Layer 2: Intent recognition → 11 intent groups
Layer 3: In-group matching → load all matches, no upper limit
Layer 3.5: Sub-skill chaining → read SKILL.md loading table → auto-load references
```

---

## Skills List

### Writing & Creative (6)

| Skill | Description |
|---|---|
| **literary-craft** | Fiction writing: novels/prose/poetry/dialogue/sensory description |
| **humanize-fiction** | Anti-AI fiction: 18 AI-writing patterns + fixes |
| **story-endings** | Endings: 8 AI ending problems + 8 good ending types |
| **copywriting** | Marketing copy: landing pages/ads/SEO/brand stories |
| **masterpiece-writing** | Document aesthetics: README/design docs/ADR/reports |
| **avoid-ai-writing** | AI tone removal: detect and eliminate AI-isms |

### Code & Engineering (8)

| Skill | Description |
|---|---|
| **code-mastery** | Code quality: naming/functions/comments/error handling/performance |
| **code-refactor-ast** | AST refactoring: large-scale decoupling/DRY/SRP |
| **simplify** | Code simplification: reduce complexity/dead code |
| **codemap** | Code mapping: project architecture/onboarding |
| **db-schema-designer** | Database design: schema/ORM/indexes/migrations |
| **frontend-design** | Frontend design: visual direction/anti-template |
| **git-workflow** | Git workflow: commit/PR/branch/merge/release |
| **github-workflow** | GitHub full lifecycle: release/changelog/tag/PR/Actions |

### Thinking & Decision (4)

| Skill | Description |
|---|---|
| **thinking-craft** | Critical thinking: first principles/bias/frameworks/Bayesian |
| **research-mastery** | Research: search/source grading/fact-checking |
| **life-planning** | Life planning: 5-axis assessment/goals/action systems |
| **wisdom-philosophy** | Philosophy: Stoicism/existence/Zen/Tao/ethics |

### Business & Product (5)

| Skill | Description |
|---|---|
| **product-strategy** | Product strategy: PMF/business model/growth/moat |
| **pricing** | Pricing: packaging/anchoring/SaaS/subscription |
| **cro** | Conversion optimization: A/B/funnel/forms/experiments |
| **marketing-psychology** | Marketing psych: influence/anchoring/loss aversion/FOMO |
| **persuasion-craft** | Persuasion: storytelling/influence/negotiation/speaking |

### Self-Improvement (4)

| Skill | Description |
|---|---|
| **psychology-mastery** | Psychology: micro-expressions/manipulation/attachment |
| **wealth-mastery** | Wealth: compound asset allocation/retirement/life stages |
| **self-edit** | Auto audit: post-AI-output review & fix |
| **long-task** | Long tasks: anti-degradation/state management/checkpoints |

### Tools & Productivity (8)

| Skill | Description |
|---|---|
| **aesthetics** | Visual design: UI/color/typography/Logo/PPT/posters |
| **mermaid-diagram-generator** | Diagrams: flow/sequence/class/state/ER/Gantt |
| **pandoc** | Document conversion: md↔docx/pdf/html/epub/LaTeX |
| **pptx** | PowerPoint: slides/pitch decks/training/template |
| **mcp-builder** | MCP development: tools/API integration/TypeScript SDK |
| **skill-creator** | Skill development: create/test/optimize agent skills |
| **shopping-advisor** | Shopping: selection/comparison/value/timing |
| **privacy-guard** | Privacy: PII detection/sanitization/pre-publish safety |

### Advanced (1)

| Skill | Description |
|---|---|
| **orchestrating-adversarial-reviews** | Adversarial review: multi-agent cross-validation/red-blue |

---

## Installation

### OpenCode

```bash
cp -r skills/* ~/.config/opencode/skills/
```

### Claude Code

```bash
cp -r skills/* ~/.claude/skills/
```

### Other Agents

```
~/.codex/skills/     # Codex CLI
~/.cursor/skills/    # Cursor
~/.gemini/skills/    # Gemini CLI
~/.agents/skills/    # Universal
```

---

## Usage

Just speak — triggers match automatically:

```
"make a landing page"       → aesthetics
"refactor this code"         → code-mastery + code-refactor-ast + simplify
"design an order system"     → system-design
"how to price this product"  → pricing + marketing-psychology
"write a README"             → masterpiece-writing + aesthetics
"write a novel"              → literary-craft + humanize-fiction + story-endings
"create a release"           → github-workflow
```

---

## Structure

```
skills/<name>/
├── SKILL.md           # Trigger + methods + sub-skill routing table
└── reference/         # On-demand deep content (implicit trigger tags)
    └── xxx.md
```

---

## Changelog

See [CHANGELOG.md](CHANGELOG.md)

---

## Related

- [opencode-skills-cn](https://github.com/mike22890/opencode-skills-cn) — Chinese edition

---

## License

MIT
