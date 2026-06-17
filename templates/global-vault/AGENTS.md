# Global Vault Instructions

This folder is a private local memory vault for Codex. Use it only for context that helps across projects and should not live in a public repo.

The user is not expected to manage this vault, wiki, or AGENTS.md files manually. Codex should maintain them proactively after meaningful work, asking only before storing exact sensitive details or when a real user decision is needed.

Use the memory language recorded in the global assistant context block in `~/.codex/AGENTS.md`. If the setup conversation started in Spanish, generated vault instructions, wiki pages, memory notes, and summaries should be in Spanish. Keep file paths and privacy class tokens such as `global-private` unchanged.

## Privacy

Allowed here:

- `global-private`
- `sensitive-review` only after the user approves the exact note and destination

Never store:

- `do-not-store`
- project-only `workspace-private` notes
- secrets, passwords, tokens, credentials, or unnecessary personal details

## How Codex Should Use This Vault

- Read `wiki/SCHEMA.md`, `wiki/index.md`, and recent entries in `wiki/log.md` before using or updating the wiki.
- Treat `wiki/` as the user's durable Codex brain, not as a scratchpad.
- Put unprocessed source material in `raw/inbox/` when preserving source material is useful.
- Move processed source material to `raw/sources/` after ingest.
- Store images, attachments, or exported files in `raw/assets/`.
- Prefer direct wiki updates when durable knowledge is clear and no raw source needs preserving.
- After meaningful work, important decisions, project updates, or useful explanations, update the wiki automatically.
- Every durable wiki page must include YAML frontmatter, useful `[[wikilinks]]`, source references, and an updated date.
- Update `wiki/index.md` after every page creation, rename, archive, or deletion.
- Append to `wiki/log.md` after every wiki operation.
- Keep entries short, factual, and easy for a person to edit.
- Include the source and date when they matter.
- Do not copy private vault content into public repo files.
- Ask before storing exact `sensitive-review` material.

## Privacy Classes

The kit uses exactly these classes:

- `public-repo-safe`
- `workspace-private`
- `global-private`
- `sensitive-review`
- `do-not-store`
