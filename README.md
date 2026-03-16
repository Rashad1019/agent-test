# Running Parallel Claude Code Agents

This project is a quick-start guide for running multiple Claude Code agents simultaneously using **git worktrees** — allowing you to parallelize development tasks across independent agent sessions.

## What This Project Does

Each Claude Code agent gets its own isolated git worktree (a separate checkout of your repo), its own context window, and its own task. The agents run in parallel without interfering with each other, and desktop notifications let you know when an agent needs your attention or finishes its work.

This setup lets you, for example:

- Run active feature development in one tab while a background agent improves test coverage
- Have one agent do a code review while another debugs a specific issue
- Scale from 2 to 5 parallel agents using the same pattern

Worktrees are stored under `.claude/worktrees/` (gitignored) and are created/removed automatically as agents start and finish.
