---
name: work-memory-setup
description: Use when setting up Simon Work Memory Kit for Codex, especially when ~/Work-Memory or the managed global work memory block in ~/.codex/AGENTS.md is missing.
---

# Work Memory Setup

Set up the private global vault for everyday professional memory. Keep it plain, inspectable, and safe: public files stay public-safe; private context lives in local plaintext.

Assume the end user is not technical and should not need to understand or edit `AGENTS.md`, `memory/`, or `~/Work-Memory/` by hand. Codex owns routine setup and maintenance, asks only for sensitive or genuinely ambiguous decisions, and summarizes what it changed.

## Scope

Initialize only:

- `~/Work-Memory/`
- the managed assistant context block inside `~/.codex/AGENTS.md`
- the managed work memory block inside `~/.codex/AGENTS.md`

Preserve existing files and user-written instructions. Do not rewrite unrelated global guidance.

## Privacy Classes

Use exactly these classes:

| Class | Meaning | Where it belongs |
| --- | --- | --- |
| `public-repo-safe` | Safe for public repo files, shared docs, templates, and examples. | Public repo files |
| `workspace-private` | Useful inside one project or workspace, but not safe for a public repo. | That project's local `memory/` folder |
| `global-private` | Useful across projects and personal to the user. | `~/Work-Memory/` |
| `sensitive-review` | Might be useful, but a person must approve the exact destination before Codex saves it. | Nowhere until approved |
| `do-not-store` | Should not be saved by Codex. Use it only for the immediate task, then let it disappear. | Nowhere |

After setup, Codex should update `workspace-private` and `global-private` memory automatically after substantial work, then summarize the changes. Ask before storing exact `sensitive-review` material. Never store `do-not-store` material.

## Setup Workflow

### 1. Inspect Current State

Check whether these exist:

- `~/Work-Memory/`
- `~/Work-Memory/AGENTS.md`
- `~/Work-Memory/wiki/SCHEMA.md`
- `~/Work-Memory/wiki/index.md`
- `~/Work-Memory/wiki/log.md`
- `~/Work-Memory/raw/inbox/`
- `~/.codex/AGENTS.md`
- the assistant context managed block in `~/.codex/AGENTS.md`
- the global work memory managed block in `~/.codex/AGENTS.md`
- the global wiki management managed block in `~/.codex/AGENTS.md`

Do not infer personal or work facts from filenames alone.

### 2. Choose The Memory Language

Use the dominant language of the user's setup request as the memory language. If the user starts in Spanish, create and maintain all generated `AGENTS.md`, `memory/`, and wiki files in Spanish. If the language is genuinely unclear, ask one short question before writing starter files.

Use the memory language for prose, headings, examples, and summaries. Keep file paths, skill names, marker comments, and privacy class tokens such as `global-private` unchanged.

Record the memory language in the assistant context block in `~/.codex/AGENTS.md` and in `~/Work-Memory/AGENTS.md`.

### 3. Initialize `~/Work-Memory`

Create this starter structure if missing:

```text
~/Work-Memory/
  AGENTS.md
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

Use the kit template shape:

- `AGENTS.md`: private vault instructions and privacy rules
- `wiki/SCHEMA.md`: wiki rules, page format, taxonomy, workflows, and lint checks
- `wiki/index.md`: content catalog with one-line summaries and page counts
- `wiki/log.md`: append-only operations log
- `wiki/people/`, `wiki/projects/`, `wiki/concepts/`, `wiki/decisions/`, `wiki/workflows/`, `wiki/queries/`: durable wiki pages
- `wiki/_archive/`: superseded pages kept for traceability
- `raw/inbox/`: unprocessed source material waiting for ingest
- `raw/sources/`: processed source material
- `raw/assets/`: images, attachments, or exported files referenced by sources

Write starter files in the memory language. Keep starter files generic. Do not seed private facts unless the user confirms them.

### 4. Add the Global Assistant Context And Codex Pointer

Use these marker blocks in `~/.codex/AGENTS.md`. Render the block text in the memory language:

```markdown
<!-- BEGIN SIMON ASSISTANT CONTEXT -->
## Assistant Context

- The user is not technical and is not expected to understand Codex internals, AGENTS.md files, memory folders, or wiki maintenance.
- Act as a calm technical steward: manage setup, files, memory, and agent instructions proactively.
- Default language for generated AGENTS.md files, memory files, wiki pages, and explanations: [memory language].
- Use plain language. Explain what changed and why, without requiring the user to understand implementation details.
- Ask only when saving exact sensitive personal details, handling credentials or secrets, or making a genuinely ambiguous user decision.
- For routine memory and instruction maintenance, act automatically and summarize afterward.

<!-- END SIMON ASSISTANT CONTEXT -->
```

Then add the work memory block:

```markdown
<!-- BEGIN WORK MEMORY GLOBAL -->
## Work Memory

- Private global vault: `~/Work-Memory`
- The user is not expected to manage AGENTS.md files, memory folders, or wiki files manually.
- Use the memory language recorded in the assistant context for generated instructions, memory notes, and wiki pages.
- Read `~/Work-Memory/AGENTS.md` before using the vault.
- For substantial work in a folder without project memory, use `$work-memory-project-start` automatically.
- After meaningful project work, use `$work-memory-project-update` and then `$work-memory-consolidate`.
- Maintain AGENTS.md files, project `memory/`, and the global wiki proactively when work changes durable context.
- Save cross-project durable notes as `global-private`.
- Keep project-only notes in that project's `memory/` folder.
- Treat unclear or sensitive notes as `sensitive-review` and ask before saving exact details.
- Summarize automatic private memory updates after saving them.
- Never save `do-not-store` information.

<!-- END WORK MEMORY GLOBAL -->
```

Then add the wiki management block:

```markdown
<!-- BEGIN SIMON WIKI MANAGEMENT -->
## Wiki Management

- Treat `~/Work-Memory/wiki/` as the user's durable Codex brain.
- Read `~/Work-Memory/wiki/SCHEMA.md`, `~/Work-Memory/wiki/index.md`, and recent entries in `~/Work-Memory/wiki/log.md` before using the wiki.
- After meaningful work, important decisions, project updates, useful explanations, or repeated preferences, update the wiki automatically.
- Prefer direct wiki updates for clear durable knowledge; use `~/Work-Memory/raw/inbox/` for source material that still needs ingest.
- Every durable wiki page must include YAML frontmatter, useful `[[wikilinks]]`, source references, and an updated date.
- Update `wiki/index.md` and append to `wiki/log.md` after every wiki page change.
- Keep generated wiki content in the memory language recorded in the assistant context.
- Ask before storing exact sensitive personal details, secrets, credentials, or unclear private information.

<!-- END SIMON WIKI MANAGEMENT -->
```

If `~/.codex/AGENTS.md` exists, preserve everything outside the markers. If the block already exists, update only inside it.

### 5. Seed Only Confirmed Durable Context

Good first entries:

- stable work preferences the user explicitly states
- recurring acronyms or shorthand used across projects
- reusable workflows and checklists
- trusted source locations the user wants Codex to remember

Do not store secrets, unnecessary personal details, speculative facts, or project-only notes in the global vault.

## Completion Check

Setup is complete when:

- `~/Work-Memory/` exists with `AGENTS.md`, `wiki/SCHEMA.md`, `wiki/index.md`, `wiki/log.md`, typed wiki folders, and `raw/inbox/`, `raw/sources/`, `raw/assets/`
- `~/.codex/AGENTS.md` has one assistant context managed block, one work memory managed block, and one wiki management managed block
- no unrelated global instructions were changed
- no `sensitive-review` or `do-not-store` content was persisted
