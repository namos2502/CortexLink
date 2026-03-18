# Changelog

All notable changes to CoFluent will be documented here.

## [1.0.1] — 2026-03-18

### Added
- `/cofluent:setup` — one-time setup command that verifies Copilot CLI is installed and authenticated, then registers CoFluent awareness in `~/.claude/CLAUDE.md` so Claude knows about CoFluent in every future session (idempotent — safe to re-run)
- `## Why CoFluent` section in README covering two key benefits: staying in flow and saving tokens on Claude by offloading subtasks to a separate `copilot -p` process

### Removed
- `/cofluent:verify` — absorbed into `/cofluent:setup`; re-run setup anytime to re-check your installation

---

## [1.0.0-beta] — 2026-03-18

Initial beta release. Core plugin structure is stable; commands and skill reference are functional but may evolve based on feedback.

### Added
- `skills/copilot-cli/SKILL.md` — core programmatic reference for the GitHub Copilot CLI; auto-loaded by Claude when invoking `copilot -p`
- `/cofluent:auto` — activates autonomous Copilot CLI mode for the session; Claude will invoke `copilot -p` automatically when appropriate
- `/cofluent:verify` — checks that Copilot CLI is installed and authenticated; guides the user through fixing any issues
- `/cofluent:ask` — delegates a question to Copilot (read-only, fast, uses `claude-haiku-4.5`)
- `/cofluent:suggest` — asks Copilot to suggest a shell command for a task
- `/cofluent:explain` — asks Copilot to explain a command, error, or code snippet
- `/cofluent:fix` — asks Copilot to fix a bug or error (read + write file permissions)
- `/cofluent:review` — runs the Copilot `/review` agent on staged diff or a specific file
- `/cofluent:help` — shows the full command reference
- `.claude-plugin/plugin.json` — plugin manifest for installation via Claude Code plugin system
- Marketplace listing in [namos2502/agent-plugins](https://github.com/namos2502/agent-plugins)

### Known limitations
- Requires GitHub Copilot CLI (`brew install copilot-cli`) — separate from `gh copilot`
- Requires active Copilot subscription and `copilot login` before use
- Commands are namespaced as `/cofluent:*` when installed as a plugin
