# Grimoire

My reusable [Claude Code](https://code.claude.com) toolkit: a **plugin marketplace** with one plugin, `grimoire`, that carries the skills, agents and templates I use across projects (Vault, Tinker, Sigil...). Improve something here once and every project gets it.

## What is inside

| Path | What |
|---|---|
| `.claude-plugin/marketplace.json` | The catalog: it lists the plugins and where they are |
| `plugins/grimoire/skills/` | The skills: `use-cases-and-criteria`, `open-questions`, `mcp-tool-design`, `writing-tests`, `ci-pipeline`, `containerize-app`, `container-delivery`, `app-telemetry`, `versioning-and-changelog` |
| `plugins/grimoire/agents/` | The agents: `spec-reviewer` (read-only reviewer of functional and technical specs) |
| `plugins/grimoire/templates/` | Files to start a project from, such as `CLAUDE.md.template` |

Skills are used as `grimoire:<skill>` (for example `grimoire:container-delivery`), and the agent as `grimoire:spec-reviewer`.

## Install

From a terminal (the same settings are used by the Claude desktop app and the VS Code extension):

```bash
claude plugin marketplace add javixulo/Grimoire
claude plugin install grimoire@grimoire
```

Or inside a session: `/plugin marketplace add javixulo/Grimoire`, then `/plugin install grimoire@grimoire`. Install it at the **user** scope (the default) so it applies to every project on that machine. Cloud sessions do not load plugins installed on a machine.

## Update

```bash
claude plugin marketplace update grimoire
claude plugin update grimoire@grimoire
```

Auto-update is off by default for marketplaces that are not Anthropic's; it can be turned on in `/plugin` → Marketplaces.

## Improve it

1. Edit the files in a clone of this repository, never in the copy Claude Code caches.
2. Try the change without publishing: `claude --plugin-dir ./plugins/grimoire`, and `/reload-plugins` after each edit.
3. Check it: `claude plugin validate ./plugins/grimoire`.
4. Commit to `main` and push. No `version` is set in `plugin.json`, so every commit counts as a new version for the people who update.

## Conventions

- Skills are written in English, are language-neutral where they can be, and each starts by asking the human what it needs before it writes anything.
- A skill that is particular to one project stays in that project's `.claude/skills/`, not here.
- Templates use `<angle brackets>` for what the project must fill in.

## License

[MIT](LICENSE) © Francisco Javier Montoro Martínez.
