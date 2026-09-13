---
name: literary-craft
description: Literary writing techniques and methods — fiction, prose, poetry, screenplays. Use when writing stories, novels, short stories, prose, essays, reviews, poetry, modern poetry, classical poetry, screenplays, dialogue, character development, plot design, dialogue writing, sensory description, mood creation, literary criticism, creative writing, content creation.
version: 2.1.0
metadata:
  author: Mike
  tags: literary fiction writing craft style sensory character plot dialogue rhythm masters
---

# Literary Craft

## When to Trigger

Keywords that trigger this skill: fiction, story, prose, poetry, screenplay, dialogue, character, plot, sensory, writing style, creative writing.

## Core Principles (6)

1. **Show, don't tell** — imply rather than state
2. **Senses over physics** — ≥3 sensory dimensions (sight/smell/touch/taste/sound)
3. **Emotion over action** — inner drives outer
4. **Negative space over excess** — what's unsaid is more powerful
5. **Rhythm over length** — alternate long and short for breathing room
6. **Dialogue over narration** — each character has a distinct voice (see `dialogue.md`)

## Mandatory Self-Check (before finishing)

- [ ] ≥ 3 sensory dimensions
- [ ] Show don't tell (don't say "he's sad" — let the body speak)
- [ ] Rhythm varies (not monotonous)
- [ ] Strategic use of negative space
- [ ] Differentiated dialogue (recognizable without names)
- [ ] Strong ending (no anticlimax)
- [ ] Reads aloud like human speech

## Load Reference (load 1 per scenario)

| User says | Loads |
|---|---|
| Learn from / style mimicry / masterworks / literary analysis | `reference/masters.md` |
| Write novel / story / plot / character / narrative structure / conflict | `reference/techniques.md` |
| Write dialogue / character voice / lines / subtext | `reference/dialogue.md` |
| Write essay / prose / review / love letter / diary / reading notes | `reference/forms.md` |

## Relationships

- **masterpiece-writing**: Document aesthetics (practical)
- **literary-craft (this)**: Literary aesthetics (artistic)
- **avoid-ai-writing**: AI tone removal (general)
- **aesthetics**: Visual aesthetics

Literary content typically pairs: masterpiece-writing + literary-craft.

## Trigger Rules

- "write a novel/story/poem" → auto-loads this skill
- "write dialogue/character voice" → + `dialogue.md`
- "write prose/love letter/diary" → + `forms.md`
- "learn from/style reference" → + `masters.md`
