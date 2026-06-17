# Maintenance

Use this routine to keep Codex memory useful, small, and private.

## During Work

- Save only context that will help future work.
- Keep each note short and practical.
- Use the memory language recorded in the global assistant context for generated instructions, memory notes, wiki pages, and summaries.
- Choose one privacy class before saving: `public-repo-safe`, `workspace-private`, `global-private`, `sensitive-review`, or `do-not-store`.
- Prefer project memory for project facts and the global vault for cross-project habits.
- Leave exact `sensitive-review` notes unsaved until the user approves the exact destination.
- Never save `do-not-store` information.

## End Of Session

Ask Codex to review what changed and update private memory automatically. Codex should summarize the class and target file after editing, and ask only for `sensitive-review` material.

Good prompt:

```text
Codex, review today's work, update only durable private memory, and summarize the class and target file for each update. Ask before saving sensitive-review material.
```

## Regular Cleanup

- Skim project `memory/glossary.md`, `memory/decisions.md`, and `memory/wiki-queue.md`.
- For the global vault, read `~/Work-Memory/wiki/SCHEMA.md`, check `wiki/index.md`, and scan recent `wiki/log.md` entries before editing.
- Remove stale notes that no longer help.
- Merge duplicate entries.
- Move unresolved source material from `memory/wiki-queue.md` into the right memory file after review.
- Process or explicitly leave files in `~/Work-Memory/raw/inbox/`; processed sources belong in `raw/sources/`.
- Confirm durable wiki pages have YAML frontmatter, useful `[[wikilinks]]`, source references, and updated dates.
- Update `wiki/index.md` and append to `wiki/log.md` after every global wiki change.
- Keep public repo docs and templates free of private memory.

## Safety Check

Before sharing or committing anything, confirm that public files contain only `public-repo-safe` content.
