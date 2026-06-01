# Repository Instructions

This is a public Codex plugin and documentation repository for `simon-codex-work-memory-kit`.

## Working Rules

- Keep memory private. Do not commit `memory/` or personal workspace state.
- Keep public instructions in `AGENTS.md`; keep private or durable local context in ignored `memory/` files.
- Use `apply_patch` for manual file edits.
- Keep edits surgical and limited to the requested scope.
- Use ASCII-only content unless a future task explicitly requires otherwise.
- Do not place private memory content in plugin files, docs, templates, examples, or public README text.

## Plugin Validation

After any manifest or skill changes, validate the plugin before reporting completion. At minimum, check that:

- `.codex-plugin/plugin.json` is valid JSON when present.
- Skill files are present at the paths referenced by the manifest.
- Public docs accurately describe the current plugin behavior.
