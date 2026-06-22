---
name: handoff-with-prompt
description: Condense a long or context-heavy conversation into a durable handoff document plus a separate paste-ready handoff prompt, so a fresh session resumes work without losing detail to auto-compaction. Tracks the original goal and any digressions, marks each work item complete/partial/pending, carries over engineering guidelines, and references existing artifacts instead of duplicating them. Use when a conversation nears ~65% context, when the user says "handoff", "do a handoff", or "wrap this up for the next session", or when work must continue in a new conversation.
argument-hint: "What will the next session focus on?"
---

# Handoff with Prompt

Produce **two** things, every time:

1. A **handoff document** — saved to a file (the durable record).
2. A **handoff prompt** — printed in chat, kept *separate* from the document. The user pastes it to start the next conversation.

## Before writing

- **Reuse an existing doc.** Look for a prior handoff for this work (default: OS temp dir, `handoff-<slug>.md`). If one exists and isn't too large (~600 lines), **update it in place** — add a dated `## Update` section and refresh the status table; don't rewrite history. Only create a new file when the existing one is too large, and then link back to the prior doc(s) at the top.
- **Capture digressions.** Record the original issue *and* every direction the work branched into, with a one-line note on why each branch matters. Don't drop side-threads.
- **Carry over engineering guidelines.** Pull from repo docs (CLAUDE.md, CONTRIBUTING, docs/) by reference, and inline any rules or instructions the user gave verbally during this conversation.
- **Don't duplicate artifacts.** Reference PRDs, plans, ADRs, issues, commits, and diffs by path or URL — never paste their content.
- **Redact** API keys, passwords, tokens, and PII.

## Where to save

Default to the OS temp dir with a stable filename (`handoff-<slug>.md`) so it can be found and reused next session. Never the workspace unless the user asks.

## Handoff document structure

```md
# Handoff — <topic> (<date>)
<!-- if continuing: link prior docs here -->

## Goal & digressions
Original objective. Then each branch the work took and why it's relevant.

## Engineering guidelines
Repo docs by path. Verbal rules from this conversation, inline.

## Status
| Item | State | Notes |
|------|-------|-------|
| ... | ✅ complete / 🟡 partial / ⬜ todo | ... |

## Done
What changed — reference commits/diffs/files, don't paste them.

## Do next
The immediate next changes.

## Pending
Not started yet.

## Leads & open threads
Loose ends, unanswered questions, ideas to investigate.

## Artifacts
Paths/URLs to PRDs, plans, ADRs, issues, key files.

## Suggested skills
Skills the next agent should invoke, and when.
```

When updating an existing doc, append:

```md
## Update — <date>
What moved since last handoff. Then refresh the Status table above.
```

## Handoff prompt (printed in chat, not saved in the doc)

```
Continue work on <topic>. Read the handoff at <path> first — it has full context.
State: <one line>. Do next: <top 1–3 items>.
Follow the engineering guidelines in that handoff.
Start by <concrete first action>.
```
