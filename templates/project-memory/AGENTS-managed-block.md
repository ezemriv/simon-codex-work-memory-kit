# AGENTS.md Managed Memory Block

Copy this block into a project's `AGENTS.md` when using local project memory.

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
