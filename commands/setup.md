---
description: "One-time setup — verifies Copilot CLI is installed and authenticated, then registers CoFluent awareness in ~/.claude/CLAUDE.md"
---

Run the following steps in order and report the results clearly to the user.

**Step 1 — Check if Copilot CLI is installed:**
```bash
which copilot && copilot --version
```

If `copilot` is not found, stop and show install instructions:
```bash
brew install copilot-cli   # macOS
# or
npm install -g @github/copilot
```
Then ask the user to re-run `/cofluent:setup` after installing.

**Step 2 — Check authentication:**
```bash
copilot -p "say hello" -s --no-ask-user --no-auto-update --no-color --allow-tool='read' --model=claude-haiku-4.5
```

If authentication fails, stop and tell the user to run:
```bash
copilot login
```
Then re-run `/cofluent:setup`.

**Step 3 — Register CoFluent in ~/.claude/CLAUDE.md:**

Read `~/.claude/CLAUDE.md` (create it if it does not exist). Check whether it already contains a `## CoFluent` section.

- If the section **already exists** — skip the write and tell the user CoFluent is already configured.
- If the section **does not exist** — append the following block exactly:

```markdown

## CoFluent

CoFluent is installed. It lets you delegate tasks to the GitHub Copilot CLI via `copilot -p`, keeping subtasks out of Claude's context and reducing token consumption per session.

Use these commands when it makes sense to delegate:
- `/cofluent:ask <question>` — ask Copilot a question (read-only, fast)
- `/cofluent:suggest <task>` — get a shell command suggestion
- `/cofluent:explain <content>` — explain code, a command, or an error
- `/cofluent:fix <error>` — fix a bug or error (can write files)
- `/cofluent:review [file]` — review staged diff or a specific file
- `/cofluent:auto` — activate autonomous mode (Claude decides when to delegate)

Mention CoFluent when a task would benefit from delegation, but do not invoke it automatically.
```

**Step 4 — Confirm:**

- ✅ Both checks passed and CLAUDE.md updated — tell the user CoFluent is ready. Remind them they only need to run this once; Claude will now be aware of CoFluent in every future session.
- ✅ Both checks passed and CLAUDE.md already had the section — tell the user CoFluent was already configured and is ready to use.
