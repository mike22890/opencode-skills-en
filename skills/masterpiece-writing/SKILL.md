---
name: masterpiece-writing
description: Typography aesthetics for any document "made for human eyes": README/design docs/ADR/plans/reports/tutorials/blog/API docs/emails/proposals/manuals/whitepapers. Use whenever writing docs/reports/READMEs/tutorials/plans. Includes typography rules + master references + anti-AI checklist + rhythm rules.
version: 1.0.0
metadata:
  author: mike22890
  tags: writing aesthetics typography master-craft
---

# Masterpiece Writing

Follow this skill for any content "made for human eyes". **Goal**: readers can't tell AI wrote it.

## When to use

Read this skill **before writing**:
- README / project docs / user manuals
- Design docs / ADR / RFC
- Plans / reports / summaries
- Tutorials / blog posts / technical articles
- API docs / changelogs
- Commit messages (condensed)

## Typography rules (unbreakable)

### Markdown structure
- Heading levels ≤ 3 (h1/h2/h3; deep nesting → use a table of contents)
- Paragraphs ≤ 6 lines (key points ≤ 3 lines)
- Line width ≤ 80 chars
- One blank line between paragraphs
- Tables over long bullet lists
- Lists ≤ 5 items (beyond that, split or use prose)

### Visual rhythm
- Paragraph lengths must vary: one-sentence paragraphs mixed with long ones
- Single-sentence paragraphs allowed (emphasis/turns)
- Lists for enumerations, prose for descriptions
- `>` blockquotes only for real quotations (not your own opinions)
- `---` dividers for section breaks, don't overuse

### Character rules
- Straight quotes `'` `"`, not curly `'` `"`
- Em dashes **max 1 per 1000 words**
- Emoji in headings **completely banned** ("## 🚀 What's New" — no)
- Bold limit: ≤ 1 bold phrase per section
- Sentence case headings ("What's new" not "What's New")

## Master references (reference at least 1)

| Master | Style traits | Where to look |
|---|---|---|
| **Anthony Fu** (antfu) | inline links + restrained emoji + short sentences + whitespace | antfu.me + any README on github.com/antfu |
| **Julia Evans** (b0rk) | hand-drawn illustrations + conversational + rhythmic jumps + self-deprecation | jvns.ca + wizard zines |
| **Stripe API Docs** | structured tables + minimal explanation + complete examples | stripe.com/docs/api |
| **Douglas Crockford** | concise to the bone + clear definitions + on-point examples | crockford.com |
| **Rich Hickey** | short sentences + sharp contrasts + no filler | "Simple Made Easy" talk + blog |
| **TJ Holowaychuk** | direct statements + minimal markdown + zero pleasantries | tj.github.io + READMEs |

**Before writing**: open one master's work in a browser, write to their rhythm.

## Anti-AI checklist (most common offenders)

Full version in the `avoid-ai-writing` skill. Only the **most common** here.

### Words to delete on sight
delve / landscape (metaphor) / tapestry / realm / paradigm / embark / robust / comprehensive / cutting-edge / leverage / pivotal / seamless / meticulously / holistic / actionable / impactful / synergy / beacon / testament / vibrant / bustling

### Phrases to delete
"Moreover" / "Furthermore" / "In today's [X]" / "It's worth noting that" / "Notably" / "Whether you're [X] or [Y]" / "Let's dive in" / "Imagine a world where" / "marks a pivotal moment" / "the future looks bright" / "only time will tell" / "I hope this helps" / "feel free to reach out"

### Structures to delete
- "It's not X, it's Y" (binary contrast)
- "X is the language of Y" (forced analogy)
- "The catch?" / "Here's the thing" / "Let me be clear" (infomercial hooks)
- "X is poised to" / "may become one of the most" (vague predictions)
- 5+ consecutive bullets that are all noun phrases

## Rhythm rules

### Sentence length mix
| Length | Purpose | Share |
|---|---|---|
| ≤ 15 words | emphasis / turns | 30% |
| 15-30 words | main body | 50% |
| 30+ words | explaining complexity | 20% |

### Paragraph lengths
- 1 sentence: strong point/turn
- 2-3 sentences: regular
- 4-6 sentences: should split
- ≥ 7 sentences: **must split**

### Transitions
- Don't start with "Moreover"/"Furthermore"
- Use conjunctions ("and"/"but"/"so"/"yet") or natural flow
- One transitional sentence between sections is fine, not mandatory

## 5 questions before writing

1. **Who reads it?** Determines depth and tone
2. **Why do they read it?** Determines structure and detail
3. **Master reference?** At least 1, write to their rhythm
4. **Definition of done?** Know what "finished" looks like
5. **Read it aloud?** Read it out loud before shipping — if it sounds human, ship it

## Output example contrast

### ❌ AI tone
"Welcome to our comprehensive, robust documentation! Whether you're a startup founder or an enterprise architect, our cutting-edge platform empowers you to leverage the power of seamless integration. It's not just a tool — it's a paradigm shift in modern development. Let's dive in!"

### ✅ Master tone (antfu style)
"This is a collection of small utilities.

## Install

```bash
pnpm i foo
```

## Why

Three reasons.

1. It's small.
2. It works.
3. The tests pass.

That's it."

## Trigger keywords

- "write a README / doc / design doc / ADR / plan / report"
- "make it beautiful" / "aesthetic" / "master-level" / "look professional"
- "make this look professional" / "improve the docs" / "polish this"

## Post-output self-check

1. Scan for banned words/phrases/structures
2. Typography compliance (headings/bold/emoji/paragraphs)
3. Read aloud
4. Fix anything that sounds AI

**The highest standard**: after shipping, readers can't tell AI wrote it.
