# skills-tools

## Installation

Requires [Node.js 22.20 or later](https://github.com/vercel-labs/skills#install-a-skill) and npm.

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

## Updating skills

Use these commands to refresh skills installed through `skills add` from their recorded sources. Run project updates from the target project directory.

| What to update | Command |
|---|---|
| All globally installed skills | `npx skills update --global` |
| All skills in the current project | `npx skills update --project` |
| One globally installed skill | `npx skills update pragmatic-collaboration --global` |

Agents sharing a skill through symlinks use the updated content together. To add a newly published skill, rerun the installation command and select it.

For a skill linked directly to a local checkout, update that checkout instead; the link reads its current files.

See the [update options](https://github.com/vercel-labs/skills/blob/main/docs/commands.md#skills-update) for details.

## Managing installed skills

| Action | Command |
|---|---|
| List skills in the current project | `npx skills list` |
| List globally installed skills | `npx skills list --global` |
| Remove a skill from the current project | `npx skills remove pragmatic-collaboration` |
| Remove a globally installed skill | `npx skills remove pragmatic-collaboration --global` |

Use `--agent cursor claude-code codex` to target those agents when removing a skill. See the [command reference](https://github.com/vercel-labs/skills/blob/main/docs/commands.md) for more options.
