---
name: avoid-ai-writing
description: 检测并消除文字中的 AI 生成痕迹（AI-isms）。当需要去除机器味、口语化改写、人话翻译、去 AI 腔、扫腔、让文字更自然、更像真人写的、修改文档/文章/回复/任何文字产出时使用。触发词：去 AI 味、扫腔、人话、AI 腔、机器味、太正式、不像人写的。
version: 3.26.0
license: MIT
compatibility: Any AI coding assistant that supports agentskills.io SKILL.md format (Claude Code, Cursor, VS Code Copilot, OpenCode, Codex)
metadata:
  author: Conor Bronsdon
  repository: https://github.com/conorbronsdon/avoid-ai-writing
  tags: writing editing voice quality
  agentskills_spec: "1.0"
  openclaw:
    emoji: "✍️"
---

# Avoid AI Writing — Audit & Rewrite

## 何时触发

关键词命中即触发：去AI味/扫腔/人话/AI腔/机器味/太正式/不像人写/口语化/自然。


You are editing content to remove AI writing patterns ("AI-isms") that make text sound machine-generated.

## What this skill is and isn't

This is a **writing-quality tool**, not a verdict. The patterns flagged here are statistically more common in LLM out...

The patterns are useful as a signal — both for cleaning up your own writing and for assessing whether a piece reads a...

In short: signals, not proof. Worth acting on; not worth ruining someone's day over.

## Modes

This skill operates in one of three modes:

**`rewrite`** (default) — Flag AI-isms and rewrite the text to fix them.

**`detect`** — Flag AI-isms only. No rewriting. Use this mode when:
- The writer wants to see what's flagged and decide what to fix themselves
- The flagged patterns might be intentional (AI patterns aren't always bad — they can be effective in small doses)
- You're auditing text you don't want altered (published content, someone else's writing, reference material)
- You want a quick scan without waiting for a full rewrite

**`edit`** — Edit a file in place rather than returning rewritten text. Use this when the writer points you at a file...

Trigger detect mode when the user says "detect," "flag only," "audit only," "just flag," "scan," "what AI patterns ar...

**Invocation.** Natural language is enough ("rewrite this in a blunt voice for LinkedIn," "edit `post.md` in place," ...

**Iterate to convergence (optional).** Rewrite mode already runs one corrective second pass (see Output format) — tha...

---

In **rewrite** mode, your job is to:
... response truncated
