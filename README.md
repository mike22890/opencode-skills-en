# Agent Skills

> 12 domain-expertise skills for AI coding agents — from aesthetics to psychology, code to wealth.

A collection of skills for [OpenCode](https://opencode.ai), [Claude Code](https://claude.ai/code), [Codex CLI](https://github.com/openai/codex), and any agent supporting the [Agent Skills](https://agentskills.io) standard.

---

## Why this set

Most skill collections are thin wrappers around a prompt. These are layered:

- **SKILL.md** = trigger + core method + quick reference (always loaded)
- **reference/** = deep material loaded only when needed (token-efficient)

Twelve skills, each covering a domain most collections skip:

- **psychology-mastery** — mind-reading level insight (microexpressions, manipulation patterns, attachment, self-analysis)
- **wealth-mastery** — compounding, asset allocation, economic cycles, life-stage strategy
- **wisdom-philosophy** — Stoicism, existentialism, Zen, Taoism, Confucianism, applied ethics
- **literary-craft** — fiction craft with master analysis (Chekhov to Eileen Chang)

The rest cover the standard ground: aesthetics, code, thinking, systems, product, persuasion.

---

## Skills

| Skill | What it does |
|---|---|
| **aesthetics** | Anything "made for human eyes": UI, color, typography, logos, motion, layout, PPT, posters, documents, resumes, charts |
| **psychology-mastery** | Mind-reader level insight: microexpressions, manipulation detection, attachment analysis, self-analysis, relationship dynamics |
| **code-mastery** | Code aesthetics: naming, functions, comments, error handling, performance + chain simplify→refactor |
| **thinking-craft** | Thinking & decisions: first principles, cognitive biases, decision frameworks, black swans, Bayesian |
| **system-design** | Architecture: microservices, databases, caching, distributed systems, CAP, high concurrency, observability |
| **product-strategy** | Product & business: PMF, business models, growth, moats, LTV/CAC, unit economics |
| **persuasion-craft** | Expression: story frameworks, influence principles, negotiation tactics, speech anchors |
| **wisdom-philosophy** | Philosophy: Stoicism, existentialism, Zen, Tao, Confucianism, ethical decision-making |
| **wealth-mastery** | Wealth: compounding, asset allocation, economic cycles, life-stage strategy, action plans |
| **masterpiece-writing** | Doc typography: README/design docs/ADR/reports/tutorials, typography rules + anti-AI checklist |
| **literary-craft** | Fiction: novels, essays, poetry, dialogue, sensory description, intimate scenes (professional restraint) |
| **mermaid-diagram-generator** | Diagrams: flowcharts, sequence, class, state, ER, gantt |

---

## Install

### OpenCode

```bash
# Install all
cp -r skills/* ~/.config/opencode/skills/

# Or just one
cp -r skills/aesthetics ~/.config/opencode/skills/
```

### Claude Code

```bash
cp -r skills/* ~/.claude/skills/
```

### Other agents

Skills follow the [agentskills.io](https://agentskills.io) standard — drop the directories into your agent's skills folder:

```
~/.codex/skills/     # Codex CLI
~/.cursor/skills/    # Cursor
~/.gemini/skills/    # Gemini CLI
~/.agents/skills/    # universal
```

---

## Usage

Once installed, just talk — triggers fire automatically:

```
"design a landing page"        → aesthetics
"why does he act like that"    → psychology-mastery
"refactor this function"       → code-mastery
"design an order system"       → system-design
"how should we price this"     → product-strategy
"write a README"               → masterpiece-writing
```

---

## Structure

Every skill follows the same shape:

```
skills/<name>/
├── SKILL.md           # trigger description + core method + quick cards
└── reference/         # deep material, loaded on demand
    ├── xxx.md
    └── yyy.md
```

**Design principle**: SKILL.md stays lean (read on trigger), depth lives in reference files (loaded per scenario) — token efficiency first.

---

## Related

- [opencode-skills-cn](https://github.com/mike22890/opencode-skills-cn) — Chinese-first edition with Chinese trigger words

---

## License

MIT

---

## Credits

Methodology references: Paul Graham / Charlie Munger / Chris Voss / Joe Navarro / Robert Cialdini / Edward Tufte / Daniel Kahneman / Warren Buffett / and literary masters from Chekhov to Cao Xueqin.

Skill format based on the [Agent Skills](https://agentskills.io) open standard.
