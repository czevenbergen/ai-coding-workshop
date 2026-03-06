# GitHub Copilot Agent Mode — Quick Reference

Reference for workshop facilitators. Covers agent mode behavior relevant to the workshop. Last updated from VS Code docs March 2026.

---

## What Agent Mode Is

Agent mode is the default Copilot Chat experience. When you select **Agent** from the agent picker, Copilot autonomously:

- Plans the work needed based on your prompt
- Reads files and gathers context from your workspace
- Edits files directly — changes are applied and saved to disk immediately
- Runs terminal commands (e.g., installing packages, starting the dev server)
- Iterates to resolve problems it encounters (reads errors, adjusts)

The agent operates end-to-end: you describe what you want, and it determines which files to read, edit, and create.

## Built-in Agents

VS Code provides three agents, selectable from the agent picker in the Chat view:

| Agent | Purpose |
|-------|---------|
| **Agent** | Autonomously plans and implements changes across files. Can run terminal commands and invoke tools. This is what participants will use most. |
| **Ask** | Answers questions about your codebase without making file changes. Uses agentic capabilities to research, but only produces text responses with optional code blocks you can apply individually. |
| **Plan** | Creates a structured step-by-step implementation plan before writing code. Can hand off the plan to Agent for implementation. |

For this workshop, participants will primarily use **Agent** mode.

## How Edits Work (Critical for Workshop)

### Changes are applied immediately

When Agent mode generates code, the changes are **applied directly to files and saved to disk**. This is not a preview — the files are modified in real time.

### Pending edits and review

After the agent makes changes:

- Files with pending edits show a **squared-dot icon** in the Explorer view and editor tabs
- Opening a changed file shows an **inline diff** highlighting what was added/removed
- The Chat view shows a **list of changed files**
- Use the **Up/Down controls** in the editor overlay to navigate between individual edits within a file

### Keep vs. Undo (per edit)

For each edit, you can:

- **Keep** — accept the edit (it becomes permanent, diff indicators disappear)
- **Undo** — reject the edit and revert that specific change

You can also **accept or reject all changes across all files at once** from the Chat view.

**Important:** Once you click **Keep** (or accept all), the change is finalized. There is no built-in "un-keep." This is why participants must review before accepting.

### Source Control integration

- **Staging** changes in Source Control automatically accepts all pending edits
- **Discarding** changes in Source Control also discards pending edits

## Checkpoints

Checkpoints are automatic snapshots VS Code creates before each chat request is processed.

- **Enable with:** `chat.checkpoints.enabled` setting
- Each chat request in the conversation has a corresponding checkpoint
- **Restore a checkpoint:** hover over a chat request in the Chat view → select **Restore Checkpoint** → confirms and reverts all file changes made after that point
- **Redo:** after restoring, you can redo the undone changes if you restored by mistake
- **Fork:** you can fork a conversation from a checkpoint to create a new session that branches from that point
- **Show file changes:** enable `chat.checkpoints.showFileChanges` to see which files changed at each checkpoint

Checkpoints are session-scoped and temporary — they do not replace version control.

## Adding Context

### Implicit context
When using Agent mode, the agent autonomously decides what context it needs — it reads files, explores the workspace, and gathers information on its own.

### Explicit context with `#`-mentions
Type `#` in the chat input to reference:
- `#file` — a specific file
- `#folder` — a folder
- `#codebase` — the entire codebase
- `#terminalSelection` — terminal output
- `#fetch` — fetch a URL
- `#githubRepo` — a GitHub repository

### Vision
You can attach images (screenshots, UI mockups) as context for your prompt.

## Custom Instructions (`copilot-instructions.md`)

A `.github/copilot-instructions.md` file in the workspace root is **automatically included in every chat request**. No manual referencing needed.

Use it for:
- Project stack and conventions
- Preferred libraries and patterns
- Architectural constraints
- What to avoid

**Priority order** (when multiple instruction sources exist):
1. Personal instructions (user-level, highest)
2. Repository instructions (`.github/copilot-instructions.md`)
3. Organization instructions (lowest)

### Other instruction file types

| File | Scope |
|------|-------|
| `.github/copilot-instructions.md` | Always-on, whole workspace |
| `AGENTS.md` | Always-on, recognized by multiple AI tools |
| `*.instructions.md` (in `.github/instructions/`) | Conditional — applied based on `applyTo` glob patterns |
| `.prompt.md` files (in `.github/prompts/`) | Manual — invoked with `/` slash commands in chat |

For this workshop, only `.github/copilot-instructions.md` is used. The other types are mentioned here for facilitator awareness.

## Prompt Files (Slash Commands)

Prompt files (`.prompt.md`) let you create reusable prompts invoked with `/name` in chat. They support:
- YAML frontmatter for configuration (agent, model, tools)
- Markdown body with instructions
- Variable substitution (`${file}`, `${selection}`, `${input:name}`)
- Tool references (`#tool:toolName`)

Not used in this workshop, but useful to know about for follow-up questions.

## Keyboard Shortcuts (macOS)

| Action | Shortcut |
|--------|----------|
| Open Chat view | `Ctrl+Cmd+I` |
| Inline Chat | `Cmd+I` |
| Quick Chat | `Shift+Option+Cmd+L` |
| Command Palette | `Shift+Cmd+P` |

## Sensitive File Protection

Agent mode prompts for approval before editing sensitive files (e.g., `.vscode/*.json`, `.env`). Configurable via `chat.tools.edits.autoApprove` setting.

## What's NOT Relevant to This Workshop

Omitted from this reference because they add complexity without teaching value for this audience:

- **Background agents** (run autonomously via CLI)
- **Cloud agents** (run on remote infrastructure, open PRs)
- **Third-party agents** (Anthropic, OpenAI external providers)
- **MCP servers** and extension-contributed tools
- **Custom agents** (`.agent.md` files)
- **Agent Skills** (`.skill.md` files)
- **Message steering/queuing** (sending messages while a request is running)
- **Hand-off between agent types**
- **Organization-level instructions**
- **Settings Sync for instructions**
- **Auto-accept edits** setting
