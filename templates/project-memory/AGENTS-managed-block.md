# AGENTS.md Managed Memory Block

Copy this block into a project's `AGENTS.md` when using local project memory.

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
