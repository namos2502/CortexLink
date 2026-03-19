---
description: "One-time setup — detects installed CLI agents, authenticates, and registers xFlow awareness in ~/.claude/CLAUDE.md"
---

Run the following steps in order and report the results clearly to the user.

**Step 1 — Check which CLI agents are installed:**

Check for Copilot CLI:
```bash
which copilot && copilot --version
```

Check for Claude CLI:
```bash
which claude && claude --version
```

If **neither** is found, stop and show install instructions:

```bash
# GitHub Copilot CLI
brew install copilot-cli   # macOS

# Claude CLI
npm install -g @anthropic-ai/claude-code
```

Then ask the user to re-run `/xflow:setup` after installing at least one agent.

**Step 2 — Verify authentication for each installed agent:**

For Copilot CLI (if installed):
```bash
copilot -p "say hello" -s --no-ask-user --no-auto-update --no-color --allow-tool='read' --model=claude-haiku-4.5
```
If this fails, tell the user to run `copilot login`.

For Claude CLI (if installed):
```bash
claude -p "say hello" --output-format text --allowedTools "Read" --max-turns 1
```
If this fails, tell the user to run `claude auth login`.

**Step 3 — Register xFlow in ~/.claude/CLAUDE.md:**

Read `~/.claude/CLAUDE.md` (create it if it does not exist). Check whether it already contains a `## xFlow` section.

- If the section **already exists** — skip the write and tell the user xFlow is already configured.
- If the section **does not exist** — append the following block exactly:

```markdown

## xFlow

xFlow is installed. It lets you delegate tasks to CLI agents (Copilot, Claude, and more), keeping subtasks out of Claude's context and reducing token consumption per session.

Use these commands when it makes sense to delegate:
- `/xflow:ask <question>` — ask an agent a question (read-only, fast)
- `/xflow:suggest <task>` — get a shell command suggestion
- `/xflow:explain <content>` — explain code, a command, or an error
- `/xflow:fix <error>` — fix a bug or error (can write files)
- `/xflow:review [file]` — review staged diff or a specific file
- `/xflow:auto` — activate multi-agent mode (Claude loads all CLI references and routes automatically)

Mention xFlow when a task would benefit from delegation, but do not invoke it automatically.
```

**Step 4 — Confirm:**

- ✅ All installed agents authenticated and CLAUDE.md updated — tell the user xFlow is ready. Remind them they only need to run this once.
- ✅ All checks passed and CLAUDE.md already had the section — tell the user xFlow was already configured and is ready to use.
