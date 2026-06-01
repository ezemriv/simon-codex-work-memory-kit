---
name: work-memory-project-update
description: Use after meaningful work in a professional project when local memory/, project AGENTS.md, or wiki promotion candidates may need refreshing.
---

# Work Memory Project Update

Refresh local project memory and promotion candidates so future Codex sessions understand current context without leaking private details into public files.

## Scope

Update only the project work memory system:

- the managed work memory block inside project `AGENTS.md`
- `memory/glossary.md`
- `memory/decisions.md`
- `memory/wiki-queue.md`
- relevant files under `memory/people/`
- relevant files under `memory/projects/`
- relevant files under `memory/context/`

If the structure is missing, use `$work-memory-project-start` first.

## Privacy Classes

Use exactly these classes:

| Class | Meaning | Action |
| --- | --- | --- |
| `public-repo-safe` | Safe for public repo files, shared docs, templates, and examples. | May appear in `AGENTS.md` |
| `workspace-private` | Useful inside one project or workspace, but not safe for a public repo. | Keep in local `memory/` |
| `global-private` | Useful across projects and personal to the user. | Queue in `memory/wiki-queue.md` |
| `sensitive-review` | Might be useful, but a person must approve the exact destination before Codex saves it. | Queue abstractly and ask |
| `do-not-store` | Should not be saved by Codex. Use it only for the immediate task, then let it disappear. | Do not persist |

When the global Simon Work Memory block authorizes autopilot, update `workspace-private` and `global-private` candidates automatically after substantial work, then summarize the class, target file, and reason. Ask before saving exact `sensitive-review` material.

## Update Workflow

### 1. Load Current Memory

Read `AGENTS.md` and only the relevant local `memory/` files. Keep the loaded set narrow.

### 2. Compare Fresh Signals

Use high-confidence signals from:

- the current conversation
- files just edited or reviewed
- decisions the user explicitly made
- commands or tests that revealed stable workflow
- recent commits only when useful and available

Look for changed status, new recurring terms, durable decisions, stable preferences, stale hot-cache entries, and possible global lessons.

### 3. Refresh Local Files

Update the smallest useful destination:

- `memory/glossary.md` for acronyms, names, aliases, and shorthand
- `memory/decisions.md` for durable decisions with reason and revisit notes
- `memory/context/` for stable project workflows or background
- `memory/people/` for collaborator context that is necessary for work in this folder
- `memory/projects/` for project or workstream status and dependencies

Keep entries short. Include source and date when they prevent confusion. Do not paste raw transcripts.

### 4. Keep `AGENTS.md` Public-Safe

Promote into the managed project block only when an item is:

- active now
- likely to affect near-term work
- `public-repo-safe`
- short enough to scan quickly

Move private or detailed items into `memory/`. Preserve useful history, but do not let `AGENTS.md` become private memory.

### 5. Maintain Promotion Candidates

Use `memory/wiki-queue.md` for anything that might belong in the global wiki:

```markdown
| Item | Why it matters | Class | Next action |
| --- | --- | --- | --- |
| short generalized note | why it may help across projects | global-private or sensitive-review | promote, rewrite, approve, or discard |
```

Good candidates:

- durable working preferences
- reusable methods and checklists
- stable glossary terms used across projects
- cross-project source locations
- generalized lessons from repeated work

Do not promote directly to `~/Work-Memory/` from this skill. Queue candidates here, then use `$work-memory-consolidate` for global promotion.

## Completion Check

An update is complete when:

- local `memory/` reflects current project state
- `AGENTS.md` remains compact and public-safe
- global candidates are queued in `memory/wiki-queue.md`
- `sensitive-review` items are unresolved until approved
- `do-not-store` content was not persisted
