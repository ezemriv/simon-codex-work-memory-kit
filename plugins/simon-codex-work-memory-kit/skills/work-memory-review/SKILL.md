---
name: work-memory-review
description: Use when reviewing work memory for sensitive-review items, redaction, forgetting requests, stale notes, duplicates, or cleanup across project and global memory.
---

# Work Memory Review

Audit, redact, forget, and clean work memory so it stays useful, current, and privacy-aware.

## Review Targets

Review only memory surfaces relevant to the request:

- `~/Work-Memory/`
- `~/.codex/AGENTS.md` managed work memory block
- project `AGENTS.md` managed work memory block
- project `memory/`

Do not edit unrelated project files while reviewing memory.

## Privacy Classes

Use exactly these classes:

| Class | Meaning | Review action |
| --- | --- | --- |
| `public-repo-safe` | Safe for public repo files, shared docs, templates, and examples. | Keep in public surfaces if useful |
| `workspace-private` | Useful inside one project or workspace, but not safe for a public repo. | Keep in project `memory/` |
| `global-private` | Useful across projects and personal to the user. | Keep in `~/Work-Memory/` if durable |
| `sensitive-review` | Might be useful, but a person must approve the exact destination before Codex saves it. | Redact, generalize, approve, or discard |
| `do-not-store` | Should not be saved by Codex. Use it only for the immediate task, then let it disappear. | Delete from all memory locations |

Default to stricter classification when evidence is weak.

## Review Modes

Use the user's request to choose the mode:

- sensitive-review: inspect queued or suspicious entries
- redaction: remove or generalize identifying detail
- forgetting: delete a fact, person, project, source, or preference from memory
- cleanup: remove stale, duplicated, or low-value entries
- audit: inspect memory and report findings before editing

Ask only if the target or deletion scope is ambiguous.

## Review Workflow

### 1. Inspect Narrowly

Search only relevant memory locations. Avoid broad scans of unrelated project files unless the user asks.

Look for:

- secrets, keys, tokens, credentials, or auth material
- raw personal data
- private health, legal, HR, financial, family, or identity details
- confidential client or company details
- exact names where roles would be enough
- stale status that could mislead future work
- duplicates that create conflicting truth

### 2. Apply the Right Action

For sensitive-review:

- summarize the risk without repeating sensitive text
- ask for explicit approval before storing exact details
- prefer generalized wording

For redaction:

- replace exact names, amounts, dates, or identifiers with safer categories when detail is not necessary
- move local context out of global memory when it is not cross-project
- keep the useful lesson when it can be made safe

For forgetting:

- remove the requested item from all work memory locations in scope
- remove aliases, backlinks, and queue items that would recreate it
- do not preserve a detailed deletion log containing the forgotten fact

For cleanup:

- merge duplicates
- demote stale public hot-cache entries into private memory when appropriate
- remove low-value notes
- keep source and last-confirmed metadata when it prevents future confusion

### 3. Verify

After edits, search the reviewed memory locations for:

- the forgotten term and obvious aliases
- secret-like patterns when sensitive cleanup was requested
- duplicate headings or repeated entries
- managed block marker integrity

If verification finds remaining sensitive material, repeat the review.

## Completion Check

Review is complete when:

- each reviewed item has a clear privacy class
- `do-not-store` content is gone
- `sensitive-review` items are redacted, generalized, approved, or discarded
- public surfaces contain only `public-repo-safe` content
- global memory contains only durable `global-private` or safer content
