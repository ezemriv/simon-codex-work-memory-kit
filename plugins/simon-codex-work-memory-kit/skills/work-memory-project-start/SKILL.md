---
name: work-memory-project-start
description: Use when starting work in a substantial professional folder or project that needs local Codex memory, especially when AGENTS.md or memory/ is missing.
---

# Work Memory Project Start

Initialize local memory for a substantial work folder while preserving `AGENTS.md` and keeping private context out of public files.

## Auto-Initialize Substantial Work Folders

Treat a folder as substantial when it is likely to matter beyond the current turn:

- a client, team, research, product, writing, operations, or personal business project
- a repository or folder with multiple work sessions of context
- a folder with decisions, collaborators, recurring terms, or deadlines
- the user says this is an ongoing project or workspace

Do not initialize scratch folders, dependency caches, generated output, vendor directories, or downloaded archives.

## Privacy Classes

Use exactly these classes:

| Class | Meaning | Where it belongs |
| --- | --- | --- |
| `public-repo-safe` | Safe for public repo files, shared docs, templates, and examples. | Public repo files |
| `workspace-private` | Useful inside one project or workspace, but not safe for a public repo. | That project's local `memory/` folder |
| `global-private` | Useful across projects and personal to the user. | Candidate for `~/Work-Memory/` |
| `sensitive-review` | Might be useful, but a person must approve the exact destination before Codex saves it. | Store only a redacted/generalized queue item; never save exact sensitive details before approval |
| `do-not-store` | Should not be saved by Codex. Use it only for the immediate task, then let it disappear. | Nowhere |

If repository visibility is unknown, treat `AGENTS.md` as `public-repo-safe` only.

## Initialization Workflow

### 1. Ensure Global Setup Exists

If `~/Work-Memory/` or the global block in `~/.codex/AGENTS.md` is missing, use `$work-memory-setup` first unless the user asked for project-local setup only.

### 2. Inspect Minimal Context

Read only enough to initialize safely:

- existing `AGENTS.md`
- `README*` or obvious project notes
- root manifests or app descriptors, if present
- the current conversation
- recent commit subjects only if this is a git repo and they clarify active work

Do not browse unrelated private files broadly. Do not infer sensitive facts from weak signals.

### 3. Create Local `memory/`

Create this starter structure if missing:

```text
memory/
  glossary.md
  decisions.md
  wiki-queue.md
  people/
  projects/
  context/
```

Use the kit templates:

- `glossary.md`: project words, acronyms, names, and shorthand
- `decisions.md`: durable project decisions
- `wiki-queue.md`: sources or notes that might become memory after review
- `people/`, `projects/`, `context/`: optional deeper local notes

If this is a git repository, ensure the root `.gitignore` contains `/memory/` before adding private `workspace-private` notes. Preserve existing ignore rules and add only that line when it is missing.

### 4. Preserve or Create `AGENTS.md`

Use these markers for the managed project block:

```markdown
<!-- BEGIN WORK MEMORY PROJECT -->
## Codex Project Memory

Codex may use the local `memory/` folder for durable project context that should not be committed or shared publicly.

Privacy classes:

- `public-repo-safe`
- `workspace-private`
- `global-private`
- `sensitive-review`
- `do-not-store`

Rules:

- Keep public repo instructions in `AGENTS.md`.
- Keep project-specific private context in `memory/`.
- Save project facts as `workspace-private` unless another class clearly applies.
- Do not copy `workspace-private` or `global-private` notes into public files.
- Treat unclear notes as `sensitive-review` and ask before saving.
- Never save `do-not-store` information.
- When proposing a memory update, Codex should show the privacy class, target file, and reason first.

<!-- END WORK MEMORY PROJECT -->
```

If `AGENTS.md` exists, preserve all content outside the markers. If it does not exist, create a minimal file with this block.

### 5. Bootstrap Only High-Confidence Context

Good first-pass entries:

- project purpose in one sentence
- active workstreams or responsibilities
- recurring acronyms and aliases
- durable decisions already visible in trusted files
- user preferences for this folder

Bad first-pass entries:

- names mentioned once
- speculative project status
- secrets, tokens, access details, or credentials
- private client/person details in `AGENTS.md`
- full meeting notes or chat transcripts

## Completion Check

Project start is complete when:

- `memory/` exists with the starter structure
- `AGENTS.md` exists and pre-existing content is preserved
- private project facts stay in `memory/`
- possible cross-project lessons are queued in `memory/wiki-queue.md`, not silently promoted
