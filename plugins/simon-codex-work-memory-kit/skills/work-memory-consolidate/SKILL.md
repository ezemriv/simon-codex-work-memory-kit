---
name: work-memory-consolidate
description: Use when consolidating project memory, wiki queue items, or repeated professional context into the global ~/Work-Memory wiki.
---

# Work Memory Consolidate

Aggressively promote durable cross-project insight into the global wiki while blocking or generalizing sensitive information.

## Goal

The global wiki should remember what helps across projects:

- stable professional preferences
- reusable workflows and checklists
- recurring people, organizations, systems, and terms
- durable relationships between projects
- trusted source locations
- generalized lessons that reduce repeated explanation

It should not become a dump of local project notes, raw conversations, or private details.

## Privacy Classes

Use exactly these classes:

| Class | Meaning | Consolidation action |
| --- | --- | --- |
| `public-repo-safe` | Safe for public repo files, shared docs, templates, and examples. | Promote only if useful across projects |
| `workspace-private` | Useful inside one project or workspace, but not safe for a public repo. | Keep local unless generalized |
| `global-private` | Useful across projects and personal to the user. | Promote to `~/Work-Memory/wiki/` |
| `sensitive-review` | Might be useful, but a person must approve the exact destination before Codex saves it. | Ask, redact, or generalize |
| `do-not-store` | Should not be saved by Codex. Use it only for the immediate task, then let it disappear. | Remove from candidates and do not store |

If a note is useful but sensitive, prefer a generalized global lesson over an exact fact.

## Consolidation Workflow

### 1. Gather Candidates

Look for candidates in:

- project `memory/wiki-queue.md`
- durable lessons in project `memory/decisions.md`
- reusable context in project `memory/context/`
- user-approved items in `~/Work-Memory/raw/`
- direct user requests to remember cross-project context

Ignore unconfirmed speculation and one-off details.

### 2. Decide Promotion

Promote when the item is:

- likely to matter in more than one project
- stable enough to survive the current task
- useful for future decisions or collaboration
- safe as `global-private` after redaction or generalization

Do not promote when the item is:

- only relevant to one folder
- temporary status
- a raw meeting note
- private information about a person that is not necessary for work
- a secret, credential, token, or access detail

### 3. Generalize Sensitive Context

Transform risky specifics into reusable lessons.

| Raw candidate | Safer global memory |
| --- | --- |
| A named client has a confidential pricing issue. | Pricing and retention details for named clients are `sensitive-review`; keep them project-local unless approved. |
| A colleague has a private personal circumstance. | Do not store private personal circumstances unless the user explicitly asks and it is necessary for respectful collaboration. |
| A proprietary metric changed on a specific date. | Remember the workflow for validating metric changes, not the confidential value. |
| A checklist worked across projects. | Store the checklist as `global-private` in the global wiki. |

Block `do-not-store` content completely.

### 4. Write to the Global Wiki

Default destination:

- append dated durable notes to `~/Work-Memory/wiki/log.md`
- update `~/Work-Memory/wiki/index.md` when a new section, source, or recurring topic should be easy to find

Use `~/Work-Memory/raw/` only when the user asks to preserve source material.

Global entries should include:

- class
- source
- note
- why keep it
- last confirmed date when helpful

### 5. Update the Local Queue

After handling a candidate, mark it in `memory/wiki-queue.md` as promoted, generalized, skipped, approved, or discarded. Do not copy full global entries back into project memory.

## Completion Check

Consolidation is complete when:

- durable cross-project items are in `~/Work-Memory/wiki/`
- local-only items stayed local
- sensitive items were blocked, generalized, or left for explicit review
- `do-not-store` items were not persisted anywhere
- the global wiki became more useful without becoming more revealing than necessary
