# Changelog

## v2.2.0 - 2026-09-14

### Changed

- **skill-creator Rewritten** — 489 → 120 lines (-75%)
  - Added 4-layer routing design guide
  - Added sub-skill / reference loading table design
  - Added trigger word design (pushy + colloquial)
  - Added pre-publish security & originality checks

### Stats

- Skills: 35 (all original)

---

## v2.1.0 - 2026-09-14

### Added

- **github-workflow** — Full GitHub management
  - Release management (semver, changelog, tags)
  - PR workflow (conventional commits, squash merge)
  - GitHub Actions basics
  - Privacy protection & security checks

---

## v2.0.3 - 2026-09-14

### Added

- **literary-craft Clean Version** — Pure literary techniques, safe and trouble-free
  - dialogue.md (character voice, dialogue techniques, subtext)
  - forms.md (short/long form templates)
  - techniques.md (show don't tell, sensory detail, pacing, negative space)
  - masters.md (Chinese & Western literary masters)

---

## v2.0.2 - 2026-09-14

### Removed

- Removed 9 duplicated public skills (not original):
  - Trail of Bits: codeql, semgrep, differential-review, fp-check, variant-analysis, sharp-edges, sarif-parsing, supply-chain-risk-auditor
  - obra/superpowers: worktrees

### Stats

- Skill count: 42 → 34 (all original)

---

## v2.0.1 - 2026-09-14

### Added

- psychology-mastery (general psychology methodology, no privacy content, safe to publish)

---

## v2.0.0 - 2026-09-14

### Breaking Changes

- **4-layer routing system** — Upgraded from single-skill matching to 4-layer auto-routing:
  - Layer 1: Scene awareness (chat/roleplay auto-loads voice-mastery)
  - Layer 2: Intent recognition (11 intent groups)
  - Layer 3: In-group matching (load all matches, no upper limit)
  - Layer 3.5: Sub-skill chaining (auto-load reference files)

- **Implicit trigger words** — Every skill and reference file now has colloquial triggers
  - Main skills: description appended with implicit triggers
  - Reference files: `<!-- 隐式触发：... -->` tags
  - No more keyword guessing — plain language just works

- **Sub-skill chaining** — After loading a main skill, its SKILL.md loading table is read and matching references are auto-loaded

- **Loading table format unified** — 27 skills have reference loading tables (table format: `| User says | Loads |`)

### New Skills (26 added)

- applying-ui-design-system, avoid-ai-writing, clonedeps, code-refactor-ast, codemap, codeql, copywriting, cro, db-schema-designer, differential-review, fp-check, frontend-design, git-workflow, marketing-psychology, mcp-builder, orchestrating-adversarial-reviews, pandoc, pptx, pricing, property-based-testing, sarif-parsing, semgrep, sharp-edges, simplify, skill-creator, supply-chain-risk-auditor, variant-analysis, worktrees

### Removed Skills (2 removed)

- psychology-mastery (re-added in v2.0.1)
- literary-craft (adult content; re-added as clean version in v2.0.3)

### Stats

| | v1.x | v2.0 |
|---|---|---|
| Trigger method | Keyword hard match | 4-layer routing + implicit triggers |
| Sub-skill | Not auto-loaded | Auto-load reference files |
| Load limit | 2-4 max | All matches, no limit |
| Reference support | Main skill only | 61 reference files + trigger tags |
| Skill count | 15 | 34 |
