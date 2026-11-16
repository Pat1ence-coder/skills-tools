# skills-tools

## Installation

Run this command from your project directory, then follow the prompts to select the skills and coding agents. Skills are installed to the current project by default.

```bash
npx skills add https://github.com/Pat1ence-coder/skills-tools
```

### Install for multiple agents

To make the selected skills available across projects in Cursor, Claude Code, and Codex, run:

```bash
npx skills add https://github.com/Pat1ence-coder/skills-tools \
  --agent cursor claude-code codex \
  --global
```

Omit `--global` to install for these agents in the current project. Choose the recommended symlink method to share one copy of a skill across agents.

### Installation directories

The `skills` CLI uses the following directories. Project paths are relative to the directory where you run the command; `~` is your home directory. Each skill has its own subdirectory.

| Agent | Project installation | Global installation (`--global`) |
|---|---|---|
| Cursor | `.agents/skills/` | `~/.cursor/skills/` |
| Claude Code | `.claude/skills/` | `~/.claude/skills/` |
| Codex | `.agents/skills/` | `~/.agents/skills/` |

See the [supported agents](https://github.com/vercel-labs/skills/blob/main/docs/agents.md) and [installation options](https://github.com/vercel-labs/skills/blob/main/docs/commands.md) for details.
