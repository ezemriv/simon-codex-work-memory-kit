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

## Language

Use the memory language recorded in the global assistant context block in `~/.codex/AGENTS.md`. Keep global wiki entries, index updates, and consolidation summaries in that language. If the block is missing, use the dominant language already present in `~/Work-Memory/AGENTS.md` or `~/Work-Memory/wiki/`.

Keep file paths, skill names, marker comments, and privacy class tokens such as `global-private` unchanged.

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

### 1. Orient To The Wiki

Before writing, read:

- `~/Work-Memory/AGENTS.md`
- `~/Work-Memory/wiki/SCHEMA.md`
- `~/Work-Memory/wiki/index.md`
- recent entries in `~/Work-Memory/wiki/log.md`

Use the schema's page types, frontmatter fields, index format, and log format.

### 2. Gather Candidates

Look for candidates in:

- project `memory/wiki-queue.md`
- durable lessons in project `memory/decisions.md`
- reusable context in project `memory/context/`
- unprocessed sources in `~/Work-Memory/raw/inbox/`
- user-approved items in `~/Work-Memory/raw/sources/`
- direct user requests to remember cross-project context

Ignore unconfirmed speculation and one-off details.

### 3. Decide Promotion

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

### 4. Generalize Sensitive Context

Transform risky specifics into reusable lessons.

| Raw candidate | Safer global memory |
| --- | --- |
| A named client has a confidential pricing issue. | Pricing and retention details for named clients are `sensitive-review`; keep them project-local unless approved. |
| A colleague has a private personal circumstance. | Do not store private personal circumstances unless the user explicitly asks and it is necessary for respectful collaboration. |
| A proprietary metric changed on a specific date. | Remember the workflow for validating metric changes, not the confidential value. |
| A checklist worked across projects. | Store the checklist as `global-private` in the global wiki. |

Block `do-not-store` content completely.

### 5. Write To Typed Wiki Pages

Prefer typed wiki pages over dumping everything into `log.md`.

Default destinations:

- `~/Work-Memory/wiki/people/` for durable people context needed for work
- `~/Work-Memory/wiki/projects/` for durable project context and relationships
- `~/Work-Memory/wiki/concepts/` for recurring terms, domains, tools, places, or ideas
- `~/Work-Memory/wiki/decisions/` for important decisions and why they were made
- `~/Work-Memory/wiki/workflows/` for stable preferences, routines, and checklists
- `~/Work-Memory/wiki/queries/` for substantial answers worth preserving

Every durable wiki page must include YAML frontmatter:

```yaml
---
title: Page Title
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: person | project | concept | decision | workflow | query | source-summary
tags: [tag]
sources: []
related: ["[[Related Page]]"]
confidence: high | medium | low
contested: false
---
```

Use `[[wikilinks]]` for related pages. Include source references for claims that come from files, links, or previous notes. Keep pages substantive; do not create empty stubs.

If preserving raw source material is useful, place it in `~/Work-Memory/raw/inbox/` first, then ingest it into wiki pages and move processed files to `~/Work-Memory/raw/sources/`.

### 6. Update Navigation And Log

After every wiki page change:

- update `~/Work-Memory/wiki/index.md`
- append an operation entry to `~/Work-Memory/wiki/log.md`
- update `updated:` dates in changed wiki files

Use the log action that fits: `ingest`, `update`, `decision`, `query-filed`, `split`, `archive`, or `delete`.

### 7. Update the Local Queue

After handling a candidate, mark it in `memory/wiki-queue.md` as promoted, generalized, skipped, approved, or discarded. Do not copy full global entries back into project memory.

## Completion Check

Consolidation is complete when:

- durable cross-project items are in `~/Work-Memory/wiki/`
- durable wiki pages have YAML frontmatter, useful wikilinks, source references, and updated dates
- `~/Work-Memory/wiki/index.md` and `~/Work-Memory/wiki/log.md` reflect the operation
- processed raw sources have been moved from `raw/inbox/` to `raw/sources/`
- local-only items stayed local
- sensitive items were blocked, generalized, or left for explicit review
- `do-not-store` items were not persisted anywhere
- the global wiki became more useful without becoming more revealing than necessary
