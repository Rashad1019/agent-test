# Running 2 Parallel Claude Code Agents

A quick-start guide for running two Claude Code agents simultaneously using git worktrees. Based on [Boris Cherny's parallel agent workflow](https://medium.com/).

---

## Prerequisites

- [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code) installed
- A git repository
- A terminal that supports multiple tabs (iTerm2, Terminal, etc.)

---

## Setup Steps

### 1. Add Worktrees to `.gitignore`

Run this once in your repo root so worktree directories don't show up as untracked files:

```bash
echo ".claude/worktrees/" >> .gitignore
```

### 2. Open Two Terminal Tabs

Open two tabs in your terminal. Rename them **1** and **2** (double-click the tab name to rename in most terminals) for easy context-switching.

### 3. Launch an Agent in Each Tab

**Tab 1** — Your active feature work:

```bash
claude -w main-feature
```

**Tab 2** — A background task (stays alive even if you close the terminal):

```bash
claude -w background-task --tmux
```

> **Tip:** Use `--tmux` for anything that'll run for more than a few minutes. The session persists even if the terminal is closed.

### 4. Initialize Dependencies in Each Worktree

Each worktree is a **clean checkout** — no `node_modules`, no `.env`, no build artifacts. Tell each agent to install dependencies before starting its task:

```
Before starting, run npm install to set up this worktree's dependencies.
Then implement: [your task here]
```

Or automate it by adding this to your `CLAUDE.md`:

```markdown
## Worktree Setup

When starting a session in a new worktree (.claude/worktrees/),
always run `npm install` before doing anything else.
Then copy `.env.example` to `.env` and ask me for any missing values.
```

### 5. Assign Clear, Self-Contained Tasks

Each agent gets its own context window and has no knowledge of the other. Give each one a task that can succeed independently.

| Tab | Role | Example Task |
|-----|------|-------------|
| 1   | Active development | Build the forgot-password flow with email via Resend, token in Redis, and tests |
| 2   | Background work | Improve test coverage for the auth module, generate API docs, or refactor a module |

**Avoid** giving an agent a task like "continue what the other agent started" — they can't see each other's work.

### 6. Set Up Desktop Notifications

Inside **either** Claude Code session, run:

```
/hooks
```

Then select **Notification** from the event list and choose **Match all**.

Claude will now send a desktop notification whenever it:

- Finishes a task and is ready for the next one
- Needs your input or approval to continue
- Encounters something it's not sure about

This frees you from watching both tabs — just respond when you get pinged.

### 7. Review and Clean Up

When an agent finishes:

- **No changes made** → worktree and branch are removed automatically when the session ends.
- **Changes exist** → Claude asks whether to keep or remove the worktree.

Manual cleanup commands:

```bash
# List all active worktrees
git worktree list

# Remove a specific worktree
git worktree remove .claude/worktrees/main-feature

# Clean up stale metadata
git worktree prune
```

---

## Quick Reference

```bash
# Start agent in a named worktree
claude -w task-name

# Start agent in background (survives terminal close)
claude -w task-name --tmux

# Let Claude auto-name the worktree
claude --worktree

# Set up notifications (inside a Claude session)
/hooks → Notification → Match all

# List active worktrees
git worktree list

# Remove a worktree
git worktree remove .claude/worktrees/task-name

# Hand off session to browser
claude --teleport
```

---

## Scaling Up

Once you're comfortable with 2 agents, you can scale to 5 using the same pattern. Cherny's recommended task distribution:

| Tab | Task Type |
|-----|-----------|
| 1   | Active feature development |
| 2   | Running and fixing tests |
| 3   | Code review and refactoring |
| 4   | Debugging a specific issue |
| 5   | Documentation or infrastructure |

> **Cost note:** On a Claude Pro subscription, each session uses your usage allowance independently. On the API, parallel agents multiply token costs proportionally.
