---
description: "Show xFlow commands and the programmatic flag reference for all supported CLI agents"
---

Show the user the available skill references (copilot-cli and claude-cli), then list these available slash commands:

| Command | What it does | Example |
|---------|-------------|---------|
| `/xflow:auto` | Activate multi-agent mode — Claude loads all CLI references and routes automatically | `/xflow:auto` |
| `/xflow:setup` | Verify CLI agents are installed and authenticated | `/xflow:setup` |
| `/xflow:ask` | Delegate a question to the best available agent | `/xflow:ask how do I reverse a string in bash?` |
| `/xflow:suggest` | Get a shell command suggestion | `/xflow:suggest delete all node_modules recursively` |
| `/xflow:explain` | Explain a command or snippet | `/xflow:explain git rebase -i HEAD~3` |
| `/xflow:fix` | Fix an error or bug | `/xflow:fix permission denied running npm install` |
| `/xflow:review` | Review staged diff or a file | `/xflow:review` or `/xflow:review src/index.ts` |
| `/xflow:help` | Show this reference | `/xflow:help` |
