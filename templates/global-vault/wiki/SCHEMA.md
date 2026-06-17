---
title: Wiki Schema
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: schema
tags: [wiki, schema]
sources: []
confidence: high
---

# Wiki Schema

This file defines how Codex maintains the user's global work-memory wiki. When generating this file for a user, write prose, headings, examples, and summaries in the memory language recorded in `~/.codex/AGENTS.md`. Keep file paths, marker comments, and privacy class tokens unchanged.

## Purpose

`~/Work-Memory/wiki/` is the user's durable Codex brain. It stores knowledge that should compound across projects, conversations, and time.

The user is not expected to maintain this wiki manually. Codex owns routine upkeep after meaningful work, important decisions, useful explanations, repeated preferences, or project updates.

## Structure

```text
~/Work-Memory/
  raw/
    inbox/
    sources/
    assets/
  wiki/
    SCHEMA.md
    index.md
    log.md
    people/
    projects/
    concepts/
    decisions/
    workflows/
    queries/
    _archive/
```

## Core Rules

- Read `SCHEMA.md`, `index.md`, and recent `log.md` entries before using or updating the wiki.
- Keep raw source material in `raw/`; durable synthesis belongs in `wiki/`.
- Use `raw/inbox/` as the queue for unprocessed source material.
- Move processed source material to `raw/sources/` when ingesting it.
- Never store secrets, credentials, tokens, or `do-not-store` material.
- Ask before storing exact `sensitive-review` details.
- Create no empty stub pages; each page must carry useful content.
- Use `[[wikilinks]]` for cross-references between wiki pages.
- Add or update `index.md` after every page creation, rename, archive, or deletion.
- Append to `log.md` after every wiki operation.

## Page Types

- `person`: durable collaborator or stakeholder context needed for work.
- `project`: cross-session project context, status, constraints, or relationships.
- `concept`: recurring terms, domains, tools, places, or ideas.
- `decision`: important decisions and why they were made.
- `workflow`: reusable checklists, routines, or operating habits.
- `query`: substantial answers worth preserving.
- `source-summary`: synthesis of a source or group of sources.

## Page Format

Every durable wiki page must start with YAML frontmatter:

```yaml
---
title: Page Title
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: person | project | concept | decision | workflow | query | source-summary
tags: [tag]
sources: [raw/sources/source-file.md]
related: ["[[Related Page]]"]
confidence: high | medium | low
contested: false
---
```

Use `contested: true` when a page contains unresolved contradictions. Use `confidence: low` for weakly supported, single-source, or fast-changing claims.

## Raw Source Format

When Codex creates a markdown source file in `raw/inbox/` or `raw/sources/`, add lightweight YAML frontmatter when the fields are known:

```yaml
---
source_url:
captured: YYYY-MM-DD
processed: false
sha256:
---
```

Use `processed: true` after ingesting the source into wiki pages. Do not edit user-provided source content just to add metadata; preserve the source as-is when metadata would be invasive or risky.

## Writing Style

- Dense bullets and short sections beat long prose.
- Keep pages scannable in about 30 seconds.
- Include dates when they prevent confusion.
- Include source references for claims that come from files, links, or previous notes.
- Prefer roles or generalized descriptions over exact personal details unless exact details are necessary and approved.

## Index Format

`wiki/index.md` is the content catalog. It must list every durable wiki page under the right section with a one-line summary.

Use this entry shape:

```markdown
- [[Page Title]] - one-line summary (N sources)
```

Keep section entries alphabetized when practical.

## Log Format

`wiki/log.md` is append-only. Use this operation format:

```markdown
## [YYYY-MM-DD] action | Subject
- Summary:
- Pages touched: [[Page One]], [[Page Two]]
- Sources:
```

Actions: `setup`, `ingest`, `update`, `decision`, `query-filed`, `lint`, `split`, `archive`, `delete`.

## Ingest Workflow

Use ingest when preserving source material matters.

1. Inspect `raw/inbox/` for unprocessed sources.
2. Read each source enough to classify it safely.
3. Decide whether it should create or update wiki pages.
4. Write or update durable pages with frontmatter, wikilinks, source references, and updated dates.
5. Move processed source files from `raw/inbox/` to `raw/sources/` and mark markdown sources as `processed: true` when practical.
6. Update `index.md`.
7. Append to `log.md`.
8. Summarize what changed for the user in plain language.

## Direct Wiki Update Workflow

Use direct updates when the durable knowledge is clear and no raw source needs preserving.

Good triggers:

- important decisions made with the user
- meaningful project updates
- repeated preferences or workflows
- useful explanations that would be painful to rederive
- stable cross-project context

After updating pages, always update `index.md` and append to `log.md`.

## Lint Checks

When reviewing wiki health, check for:

- missing required frontmatter
- pages missing from `index.md`
- broken `[[wikilinks]]`
- orphan pages with no meaningful incoming or outgoing links
- stale pages whose `updated` date no longer reflects known context
- `confidence: low` pages that need corroboration or cleanup
- `contested: true` pages that need user review
- pages over about 200 lines that should be split
- unprocessed files left in `raw/inbox/`

Report issues in plain language and fix routine issues automatically when safe.
