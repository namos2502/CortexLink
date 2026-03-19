---
description: "Activate autonomous multi-agent mode — Claude will know when and how to invoke copilot -p or claude -p for the rest of this session"
---

Load the copilot-cli skill reference and the claude-cli skill reference into your context for this session.

From now on, whenever a task would benefit from delegating to an available CLI agent, use the appropriate agent with the correct programmatic flags from the skill references — without the user needing to ask explicitly.

**Routing guidance:**
- Use `copilot -p` for GitHub-specific tasks (repo questions, PR reviews, git workflows, GitHub Actions)
- Use `claude -p` for general code tasks (explanations, fixes, suggestions, analysis)
- When in doubt, prefer the agent that is installed and authenticated

Confirm to the user that multi-agent mode is active and that you will autonomously delegate tasks when appropriate. Remind them that explicit commands are still available if they prefer direct control:

- `/xflow:ask` — ask an agent a question
- `/xflow:suggest` — get a shell command suggestion
- `/xflow:explain` — explain a command or snippet
- `/xflow:fix` — fix a bug or error
- `/xflow:review` — review code
- `/xflow:setup` — verify CLI agents are installed and authenticated
