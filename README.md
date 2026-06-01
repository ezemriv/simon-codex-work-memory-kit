# simon-codex-work-memory-kit

Plaintext memory for everyday professional work

`simon-codex-work-memory-kit` is a Codex-first plugin for keeping durable work context in simple local files. It helps Codex remember project conventions, current priorities, operating notes, and private context without adding a database, hosted service, or workflow platform.

## Origin

This kit began from Simon, an architect friend who had just installed Codex and wanted help across several interrelated architecture and interior-design projects without becoming an AI tools specialist.

## What It Gives You

- A local Codex plugin with skills for setup, project memory, consolidation, and review.
- A two-tier memory model that separates project working memory from a private global vault.
- An aggressive-but-private autopilot that captures useful context while keeping personal or sensitive details local.
- A no-infrastructure promise: plaintext files, your editor, and Codex.
- A Codex-only v1, intentionally scoped before supporting other agents.

## 10-Minute Setup

1. Clone this repo and enter it:

   ```bash
   git clone <repo-url> simon-codex-work-memory-kit
   cd simon-codex-work-memory-kit
   ```

2. Register the repo-local marketplace and install the plugin:

   ```bash
   codex plugin marketplace add .
   codex plugin add simon-codex-work-memory-kit@simon-work-memory
   ```

3. Start a new Codex thread and say:

   ```text
   Use $work-memory-setup to initialize Simon Work Memory Kit.
   ```

4. Codex creates `~/Work-Memory` and adds a bounded managed block to `~/.codex/AGENTS.md`.
5. In each substantial work folder, Codex can then use `$work-memory-project-start` automatically, keep project memory in `memory/`, and consolidate cross-project lessons into the global vault.

## Two-Tier Memory Model

This kit uses two simple layers:

1. Project working memory in each substantial folder.
   A bounded block in `AGENTS.md` tells Codex where project memory lives. The private `memory/` folder stores glossary terms, decisions, project context, people, and promotion candidates.
2. Global work memory in `~/Work-Memory`.
   This private vault stores cross-project lessons, reusable workflows, stable preferences, and a small wiki index/log so Codex can recover context across unrelated folders.

The project layer is the hot working cache. The global vault is the long-term commonplace book.

## Aggressive-But-Private Autopilot

Codex should be proactive about noticing reusable context: decisions, conventions, gotchas, glossary terms, collaborators, source locations, and recurring workflows. The kit encourages capturing that context in private memory when it helps future work, while keeping public repository files free of personal notes and sensitive details.

The default stance is simple: remember more privately, publish less publicly. Sensitive or unclear items are blocked, generalized, or sent to review.

## Privacy Classes

The kit uses exactly five classes:

- `public-repo-safe`: safe for public docs, templates, and examples.
- `workspace-private`: useful only inside one project folder.
- `global-private`: useful across projects in `~/Work-Memory`.
- `sensitive-review`: useful maybe, but requires review before exact storage.
- `do-not-store`: use for the immediate task only, then discard.

## No-Infrastructure Promise

There is no server to deploy, no database to migrate, no account to provision, and no hidden sync layer. The memory system is just plaintext files arranged so Codex and humans can both use them.

## Codex-only v1

Version 1 is for Codex. The repo may document ideas that later translate to other agents, but the first public shape stays focused on Codex behavior, Codex plugin documentation, and local plaintext memory.

## Validate The Plugin

After changing plugin metadata or skills, validate with the plugin validator from your local `plugin-creator` skill:

```bash
python3 ~/.codex/skills/.system/plugin-creator/scripts/validate_plugin.py plugins/simon-codex-work-memory-kit
```

If your Python environment does not have PyYAML installed, run the same command from an environment that does. Codex plugin installation is the practical smoke test:

```bash
codex plugin marketplace add .
codex plugin add simon-codex-work-memory-kit@simon-work-memory
```

## License

MIT. See `LICENSE`.
