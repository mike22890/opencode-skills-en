# Changelog

## v4.0.0 - 2026-09-14

### Breaking Changes

- **All skills now have implicit triggers** — every skill has:
  - 何时触发 section with colloquial trigger words
  - `<!-- 隐式触发 -->` tags on all reference files
  - Loading tables mapping user phrases to references
  - Pushy descriptions for better auto-matching

- **4-layer routing system** — all skills support:
  - Layer 1: Scene awareness (auto-loads voice-mastery for chat)
  - Layer 2: Intent recognition (11 intent groups)
  - Layer 3: In-group matching (load all matches, no limit)
  - Layer 3.5: Sub-skill chaining (auto-load references)

### Removed

- All Trail of Bits security skills (public duplicates)
- roleplay-craft (adult content)
- voice-mastery (privacy)
- worktrees (obra/superpowers duplicate)

### Stats

- Skills: 40 (all original)
- Reference files: all tagged with implicit triggers
- Loading tables: all skills have them

---

## v3.1.0 - 2026-09-14

### Added

- **story-endings** — 8 AI ending problems + 8 good ending types

---

## v3.0.0 - 2026-09-14

### Added

- **self-edit** — auto post-processing audit & fix
- **long-task** — long task anti-degradation & state management
- **privacy-guard** — privacy leak prevention & sanitization
- **humanize-fiction v2.0** — 10→18 AI-writing patterns

---

## v2.1.0 - 2026-09-14

### Added

- **github-workflow** — Full GitHub management

---

## v2.0.3 - 2026-09-14

### Added

- **literary-craft clean version** — pure literary techniques

---

## v2.0.2 - 2026-09-14

### Removed

- 9 duplicated public skills

---

## v2.0.0 - 2026-09-14

### Breaking Changes

- 4-layer routing system
- Implicit trigger words
- Sub-skill chaining

### Stats

| | v1.x | v4.0 |
|---|---|---|
| Trigger | Keyword match | 4-layer + implicit |
| Sub-skill | Not loaded | Auto-loaded |
| Load limit | 2-4 | No limit |
| Skills | 15 | 40 |
