# Privacy Model

Use this model before Codex remembers anything. The goal is autopilot for useful private memory, with hard brakes for sensitive or unsafe material.

Do not invent extra privacy classes. The kit uses exactly these:

| Class | Meaning | Where it belongs |
| --- | --- | --- |
| public-repo-safe | Safe for public repo files, shared docs, templates, and examples. It contains no personal, customer, secret, or private work details. | Public repo files |
| workspace-private | Useful inside one project or workspace, but not safe for a public repo. | That project's local `memory/` folder |
| global-private | Useful across projects and personal to the user. | The user's private global vault |
| sensitive-review | Might be useful, but a person must approve the exact destination before Codex saves it. | Nowhere until approved |
| do-not-store | Should not be saved by Codex. Use it only for the immediate task, then let it disappear. | Nowhere |

## Routing Rules

- Public docs, templates, examples, and plugin files may only contain `public-repo-safe` information.
- Project memory files are for `workspace-private` information.
- The global vault is for `global-private` information.
- If the right class is unclear, treat the note as `sensitive-review` and ask before saving exact details.
- Secrets, passwords, tokens, credentials, unnecessary personal details, and anything the user says not to remember are `do-not-store`.

## Codex Habit

When the global Simon Work Memory block is installed, Codex may update `workspace-private` and `global-private` memory automatically after substantial work. It should summarize what changed afterward.

Before saving exact `sensitive-review` material, Codex must say:

1. The privacy class.
2. The target file.
3. A one-sentence reason the note is worth keeping.

If any part feels uncertain, Codex should generalize, redact, or ask first.
