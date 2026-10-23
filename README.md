# read-before-write

**Every AI edits files without reading them first. This skill fixes that.**

Free and open source · MIT Licence · Built by [Speedrun AI Labs](https://www.speedrunlab.ai), Sydney, Australia

---

## The problem

On the morning this skill was written, two things happened within an hour of each other:

1. Our in-house AI agent tried to update a memory file — and silently overwrote it from scratch instead of editing it.
2. Claude.ai, in a separate session, did the exact same thing to a different file.

Same mistake. Two different AI systems. One morning.

This is not a rare edge case. Every LLM — Claude, ChatGPT, Gemini, all of them — defaults to rewriting files instead of patching them. They don't read what's already there. They just write over it. Silently. Without flagging the conflict.

A contract lawyer reads the whole document before changing a word. A financial adviser reads the existing portfolio before recommending changes. An accountant reads the existing ledger before posting an entry.

Your AI agent should do the same. Now it can.

---

## What it does

Installs a mandatory read-before-write discipline into any AI agent:

- **Read first, always** — the full file, before any edit
- **Patch, don't replace** — surgical edits only; never rewrite the whole file unless explicitly instructed
- **Flag conflicts** — if existing content contradicts the intended change, surface it before proceeding
- **Hard stop on unreadable files** — if the file can't be read for any reason, the agent stops and says so; it does not proceed blind

---

## Install

### Claude Code
```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Speedrunlab/read-before-write.git ~/.claude/skills/read-before-write
```
Then run: `/read-before-write`

### OpenClaw
```bash
mkdir -p ~/.openclaw/skills
git clone https://github.com/Speedrunlab/read-before-write.git ~/.openclaw/skills/read-before-write
```
OpenClaw picks it up automatically on next session.

### Any LLM (ChatGPT, Gemini, etc.)
Copy the contents of `SKILL.md` into your system prompt or custom instructions.

---

## Compatibility

| Tool | Supported |
|------|-----------|
| Claude Code | ✅ |
| OpenClaw | ✅ |
| ChatGPT (custom instructions) | ✅ |
| Gemini (system prompt) | ✅ |
| Any LLM with system prompt access | ✅ |

---

## Part of the Speedrun AI Labs Skill Library

This skill is part of the open-source skill library at [speedrunlab.ai](https://www.speedrunlab.ai).

Other skills:
- [/reverse-engineer-anything-self-learning-loop](https://github.com/Speedrunlab/reverse-engineer-anything-self-learning-loop), examine a product you are authorised to rebuild, build your own, and improve it against the original until it is 100% there
- [/deep-audit](https://github.com/Speedrunlab/deep-audit) — four-phase code auditor with evidence standards
- [/no-slop-writing](https://github.com/Speedrunlab/no-slop-writing) — eliminates AI-speak from generated text (American English)
- [/no-slop-writing-au](https://github.com/Speedrunlab/no-slop-writing-au) — same, Australian English edition

---

## Licence

MIT. Free to use, modify, and distribute.

---

*Built in Sydney by Speedrun AI Labs — where we caught this bug the hard way.*
