---
name: work-memory-setup
description: Use when setting up Simon Work Memory Kit for Codex, especially when ~/Work-Memory or the managed global work memory block in ~/.codex/AGENTS.md is missing.
---

# Work Memory Setup

Set up the private global vault for everyday professional memory. Keep it plain, inspectable, and safe: public files stay public-safe; private context lives in local plaintext.

## Scope

Initialize only:

- `~/Work-Memory/`
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

After setup, Codex may update `workspace-private` and `global-private` memory automatically after substantial work, then summarize the changes. Ask before storing exact `sensitive-review` material. Never store `do-not-store` material.

## Setup Workflow

### 1. Inspect Current State

Check whether these exist:

- `~/Work-Memory/`
- `~/Work-Memory/AGENTS.md`
- `~/Work-Memory/wiki/index.md`
- `~/Work-Memory/wiki/log.md`
- `~/.codex/AGENTS.md`
- the global work memory managed block in `~/.codex/AGENTS.md`

Do not infer personal or work facts from filenames alone.

### 2. Initialize `~/Work-Memory`

Create this starter structure if missing:

```text
~/Work-Memory/
  AGENTS.md
  raw/
  wiki/
    index.md
    log.md
```

Use the kit template shape:

- `AGENTS.md`: private vault instructions and privacy rules
- `wiki/index.md`: short navigation for cross-project context
- `wiki/log.md`: dated durable notes
- `raw/`: unprocessed source material only when the user asks

Keep starter files generic. Do not seed private facts unless the user confirms them.

### 3. Add the Global Codex Pointer

Use these markers in `~/.codex/AGENTS.md`:

```markdown
<!-- BEGIN WORK MEMORY GLOBAL -->
## Work Memory

- Private global vault: `~/Work-Memory`
- Read `~/Work-Memory/AGENTS.md` before using the vault.
- For substantial work in a folder without project memory, use `$work-memory-project-start` automatically.
- After meaningful project work, use `$work-memory-project-update` and then `$work-memory-consolidate`.
- Save cross-project durable notes as `global-private`.
- Keep project-only notes in that project's `memory/` folder.
- Treat unclear notes as `sensitive-review` and ask before saving.
- Summarize automatic private memory updates after saving them.
- Never save `do-not-store` information.

<!-- END WORK MEMORY GLOBAL -->
```

If `~/.codex/AGENTS.md` exists, preserve everything outside the markers. If the block already exists, update only inside it.

### 4. Seed Only Confirmed Durable Context

Good first entries:

- stable work preferences the user explicitly states
- recurring acronyms or shorthand used across projects
- reusable workflows and checklists
- trusted source locations the user wants Codex to remember

Do not store secrets, unnecessary personal details, speculative facts, or project-only notes in the global vault.

## Completion Check

Setup is complete when:

- `~/Work-Memory/` exists with `AGENTS.md`, `wiki/index.md`, `wiki/log.md`, and `raw/`
- `~/.codex/AGENTS.md` points to the vault through one managed block
- no unrelated global instructions were changed
- no `sensitive-review` or `do-not-store` content was persisted
