# CoFluent

> Two AIs walk into a terminal. One knows the flags. The other learns them.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![GitHub](https://img.shields.io/badge/GitHub-namos2502%2FCoFluent-181717?logo=github)](https://github.com/namos2502/CoFluent)

You know the feeling. You are deep in a vibe coding session — ideas flowing, Claude keeping up — and then you need to hand something off to Copilot. Suddenly you are out of the zone, hunting for the right flags, checking docs, figuring out what `--allow-tool` even accepts. The flow breaks.

CoFluent fixes that.

Introducing **CoFluent** (copilot-fluent) — a cross-agent workflow plugin for Claude Code. It gives Claude the full GitHub Copilot CLI reference — flags, permissions, patterns, model choices — baked right in. Install it once, and Claude already knows how to speak Copilot. No interruptions, no setup tax, no context switching. You stay in the zone and Claude handles the handoff.

The way it should work.

## Why CoFluent

**Stay in flow.** No context switching, no flag hunting, no setup tax. Claude already knows the full Copilot CLI programmatic reference — flags, permissions, model choices — baked right in.

**Save tokens on Claude.** Every task you delegate to Copilot runs in a separate `copilot -p` process. Only the final answer comes back into Claude's context window — not the reasoning chain, not the tool calls, not the intermediate output. This keeps Claude's context lean, reduces token consumption per session, and stretches your quota further.

## Get started

Before installing, make sure you have the [GitHub Copilot CLI](https://docs.github.com/en/copilot/how-tos/copilot-cli) set up. It is a standalone tool — not the same as `gh copilot`:

```bash
brew install copilot-cli
copilot login
```

Then install CoFluent from inside Claude Code:

```
/plugin marketplace add namos2502/agent-plugins
/plugin install cofluent@agent-plugins
/reload-plugins
```

Then run setup once:

```
/cofluent:setup
```

This verifies Copilot CLI is installed and authenticated, and registers CoFluent awareness in your `~/.claude/CLAUDE.md` so Claude knows about it in every future session.

Requires Claude Code v1.0.33+.

## Commands

| Command | What it does |
|---------|-------------|
| `/cofluent:setup` | One-time setup — verifies install, authenticates, and registers CoFluent in your `~/.claude/CLAUDE.md` |
| `/cofluent:auto` | Activates copilot-aware mode — Claude handles `copilot -p` calls on its own |
| `/cofluent:ask` | Asks Copilot a question |
| `/cofluent:suggest` | Gets a shell command for a task |
| `/cofluent:explain` | Explains a command, error, or snippet |
| `/cofluent:fix` | Fixes a bug or error (reads and writes files) |
| `/cofluent:review` | Reviews staged diff or a specific file |
| `/cofluent:help` | Shows this reference |

### Pick your style

**Hands-off** — run `/cofluent:auto` once and let Claude decide when to reach for Copilot. Good for longer sessions where you just want things to work.

**Hands-on** — use individual commands to point Claude at a specific task. You stay in control of every delegation.

## Under the hood

CoFluent ships a single skill file — `skills/copilot-cli/SKILL.md` — that Claude loads as its Copilot CLI reference. It covers the right flags for non-interactive use, tool permissions, model selection, and ready-to-run invocation patterns.

The base pattern Claude always follows:

```bash
copilot -p "..." -s --no-ask-user --no-auto-update --no-color --allow-tool='read'
```

Full flag reference in the [official docs](https://docs.github.com/en/copilot/reference/copilot-cli-reference/cli-programmatic-reference).

## License

MIT
