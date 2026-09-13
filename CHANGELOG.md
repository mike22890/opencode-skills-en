# Changelog

## v2.0.1 - 2026-09-14

### Updated

- Added psychology-mastery back (42 skills total)

---

## v2.0.0 - 2026-09-14

### Breaking Changes

- **4-layer routing system** — Upgraded from single-skill matching to 4-layer auto-routing:
  - Layer 1: Scene awareness (chat/roleplay auto-loads voice-mastery)
  - Layer 2: Intent recognition (11 intent groups)
  - Layer 3: In-group matching (load all matches, no upper limit)
  - Layer 3.5: Sub-skill chaining (auto-load reference files)

- **Implicit trigger words** — Every skill and reference file now has colloquial triggers
  - Main skills: description appended with implicit triggers (e.g., "too messy", "ugly", "help me choose")
  - Reference files: `<!-- 隐式触发：... -->` tags
  - No more keyword guessing — plain language just works

- **Sub-skill chaining** — After loading a main skill, its SKILL.md loading table is read and matching references are auto-loaded
  - Example: "write intimate dialogue in a novel" → literary-craft + techniques.md + dialogue.md + intimacy.md
  - One task can trigger multiple references, auto-combined

- **Loading table format unified** — All reference loading tables standardized to table format: `| User says | Loads |`
  - 27 skills now have reference loading tables
  - Covers routing rules for all sub-files

### New Skills (26 added)

- applying-ui-design-system — Design system selection & implementation
- avoid-ai-writing — AI writing pattern detection & removal
- clonedeps — Clone third-party deps for source reading
- code-refactor-ast — AST-based large-scale refactoring
- codemap — Code repository mapping / onboarding
- codeql — CodeQL SAST scanning
- copywriting — Marketing copy
- cro — Conversion rate optimization
- db-schema-designer — Database schema design
- differential-review — Security diff review
- fp-check — Vulnerability verification / false positive elimination
- frontend-design — Frontend visual design
- git-workflow — Git workflow
- marketing-psychology — Marketing psychology
- mcp-builder — MCP server development
- orchestrating-adversarial-reviews — Multi-agent adversarial review
- pandoc — Document format conversion
- pptx — PowerPoint creation
- pricing — Pricing strategy
- property-based-testing — Property-based testing / fuzzing
- sarif-parsing — SARIF result parsing
- semgrep — Semgrep scanning
- sharp-edges — Dangerous API identification
- simplify — Code simplification
- skill-creator — Skill development
- supply-chain-risk-auditor — Supply chain auditing
- variant-analysis — Variant analysis
- worktrees — Git Worktree management

### Removed Skills (2 removed)

- psychology-mastery — Privacy considerations (re-added in v2.0.1)
- literary-craft — Adult content, not publicly distributed

### Old vs New

| | v1.x | v2.0 |
|---|---|---|
| Trigger method | Keyword hard match | 4-layer routing + implicit triggers |
| Sub-skill | Not auto-loaded | Auto-load reference files |
| Load limit | 2-4 max | All matches, no limit |
| Reference support | Main skill only | 61 reference files + trigger tags |
| Skill count | 15 | 42 |
