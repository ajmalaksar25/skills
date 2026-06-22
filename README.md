# skills

[![skills.sh](https://skills.sh/b/ajmalaksar25/skills)](https://skills.sh/ajmalaksar25/skills)

My personal agent skills. Agent-neutral — a skill is just a `SKILL.md`, so it works in any of the 70+ coding agents the [`skills`](https://github.com/vercel-labs/skills) CLI supports (Claude Code, Codex, Cursor, Cline, Gemini CLI, Windsurf, Copilot, …).

## Skills

| Skill | What it does |
|-------|--------------|
| [handoff-with-prompt](skills/handoff-with-prompt/) | Condense a long conversation into a durable handoff document plus a separate paste-ready handoff prompt, so a fresh session resumes work without losing detail to compaction. |

## Install

Install to every agent the CLI detects:

```sh
npx skills add ajmalaksar25/skills -g
```

Or target specific agents:

```sh
npx skills add ajmalaksar25/skills -g -a claude-code -a cursor -a codex
```

A global (`-g`) install may print `PromptScript does not support global skill installation`. PromptScript only supports project-level installs — it's a known CLI bug ([vercel-labs/skills#1352](https://github.com/vercel-labs/skills/issues/1352)) and the other agents install fine. For PromptScript itself, install at project level (drop `-g`, run inside the project):

```sh
npx skills add ajmalaksar25/skills -a promptscript
```

Or symlink a skill straight into your skills directory:

```sh
ln -s "$PWD/skills/handoff-with-prompt" ~/.claude/skills/handoff-with-prompt
```
