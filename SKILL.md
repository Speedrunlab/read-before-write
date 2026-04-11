---
name: read-before-write
description: Enforces read-before-write discipline for all file edits. Activates whenever the agent is about to edit, update, append, or overwrite any existing file. Prevents blind overwrites, silent regressions, and content loss. Use when: working with any existing file — memory files, configs, code, documents. The rule: read the full file before changing a single line.
---

# Read-Before-Write

Every AI edits files without reading them first. This skill fixes that.

## The Rule

Never touch a file without reading it in full first. No exceptions.

This applies to:
- Code files
- Memory and context files
- Config files
- Documentation
- Any existing file of any kind

## The Workflow

1. **Read the full file** before making any change
2. **Identify conflicts** — does the intended change contradict or overwrite existing content?
3. **If conflict found** — flag it before proceeding: "I found X in the file that conflicts with Y. Which takes precedence?"
4. **If no conflict** — apply the change as a targeted edit, not a full rewrite
5. **Prefer surgical edits** — patch the specific lines that need changing. Never rewrite the whole file unless an explicit full replacement was requested.

## Diff/Patch Principle

The mental model: Git diffs. You are applying a patch, not replacing the file.

- Use targeted edit tools for specific replacements
- Use write/create only when creating a brand new file, or when an explicit full replacement was approved
- If unsure whether a file exists: check first, then write

## The Failure Mode This Prevents

❌ User says "update the config file" → agent writes a new file from scratch, wiping all existing settings
✅ User says "update the config file" → agent reads current content, identifies the specific lines to change, applies a targeted edit

The difference: one destroys work silently. The other preserves it.

## If the File Cannot Be Read

If reading is blocked for any reason (tool limit, permission error, file too large):
- Stop
- Say: "Can't read [filename] — [reason]. Not touching it until I can."
- Do not proceed with the write

## The Analogy

A contract lawyer reads the whole document before changing a word. A financial adviser reads the existing portfolio before recommending changes. An accountant reads the existing ledger before posting an entry.

Your AI agent should do the same.

## Compatibility

Works with Claude Code, OpenClaw, ChatGPT, Gemini, and any LLM that accepts a system prompt or custom instructions.
