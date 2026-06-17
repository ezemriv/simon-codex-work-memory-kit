---
name: work-memory-project-start
description: Use when starting work in a substantial professional folder or project that needs local Codex memory, especially when AGENTS.md or memory/ is missing.
---

# Work Memory Project Start

Initialize local memory for a substantial work folder while preserving `AGENTS.md` and keeping private context out of public files.

Assume the end user is not technical and should not need to manage `AGENTS.md`, `memory/`, or wiki files manually. Codex should maintain these files proactively during normal work, asking only before saving sensitive exact details or when a real user decision is needed.

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

## Language

Use the memory language recorded in the global assistant context block in `~/.codex/AGENTS.md`. If that block is missing, use the dominant language of the current conversation. If the user starts in Spanish, create and maintain project `AGENTS.md`, `memory/`, and wiki queue files in Spanish.

Use the memory language for prose, headings, examples, and summaries. Keep file paths, skill names, marker comments, and privacy class tokens such as `workspace-private` unchanged.

## Initialization Workflow

### 1. Ensure Global Setup Exists

If `~/Work-Memory/`, `~/Work-Memory/wiki/SCHEMA.md`, the global work memory block, or the global wiki management block in `~/.codex/AGENTS.md` is missing, use `$work-memory-setup` first unless the user asked for project-local setup only.

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

Write starter headings and boilerplate in the memory language.

If this is a git repository, ensure the root `.gitignore` contains `/memory/` before adding private `workspace-private` notes. Preserve existing ignore rules and add only that line when it is missing.

### 4. Preserve or Create `AGENTS.md`

Use these markers for the managed project block:

```markdown
<!-- BEGIN WORK MEMORY PROJECT -->
## Codex Project Memory

Codex uses the local `memory/` folder for durable project context that should not be committed or shared publicly.

The user is not expected to manage this `AGENTS.md` file, the `memory/` folder, or wiki promotion by hand. Codex is responsible for routine maintenance.

Use the memory language from the global assistant context for generated instructions, memory notes, wiki queue entries, and user-facing summaries.

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
- After meaningful work, update project memory automatically and queue useful cross-project lessons for the global wiki.
- Use `$work-memory-consolidate` when queued lessons, decisions, or reusable explanations should become durable global wiki pages.
- Treat unclear or sensitive notes as `sensitive-review` and ask before saving exact details.
- Never save `do-not-store` information.
- Summarize automatic memory updates with the privacy class, target file, and reason.

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
