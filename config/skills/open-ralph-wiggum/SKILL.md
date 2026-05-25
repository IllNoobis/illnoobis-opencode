---
name: open-ralph-wiggum
description: >
  Use this skill whenever a user wants to run, install, configure, or understand open-ralph-wiggum (ralph).
  This skill can be used by any AI assistant or IDE agent (GitHub Copilot, Claude Code, Cursor, Windsurf, etc.).
  Triggers on: "ralph", "ralph wiggum", "agentic loop", "iterative AI loop", "autonomous coding loop",
  "how to install ralph", "how to use ralph with Claude Code / Codex / Copilot / Cursor Agent / OpenCode",
  "ralph --agent", "ralph --tasks", "ralph --status", "--max-iterations", "--rotation",
  "how do I run ralph in VS Code / Cursor / JetBrains / Neovim",
  or any question about looping an AI coding agent until a task is done.
  Even if the user doesn't say "ralph" explicitly — if they want to run an AI agent in a loop
  until a promise tag appears in its output, use this skill.
---

# Open Ralph Wiggum

**Open Ralph Wiggum** (`ralph`) wraps any supported AI coding agent in an autonomous loop: it sends the same prompt on every iteration, and the agent self-corrects by observing the state of the repo. The loop ends when the agent outputs a configurable completion promise (e.g. `<promise>COMPLETE</promise>`).

Supported agents: **Claude Code**, **OpenAI Codex**, **GitHub Copilot CLI**, **Cursor Agent**, **OpenCode** (default).

---

## Installation

### Prerequisites

- [Bun](https://bun.sh) runtime
- At least one of these AI coding agent CLIs installed and authenticated:
  - `claude` — [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
  - `codex` — [OpenAI Codex CLI](https://github.com/openai/codex)
  - `copilot` — [GitHub Copilot CLI](https://github.com/github/copilot-cli)
  - `cursor-agent` — [Cursor Agent CLI](https://cursor.com/cli/)
  - `opencode` — [OpenCode](https://opencode.ai)

### npm (recommended)

```bash
npm install -g @th0rgal/ralph-wiggum
```

### Bun

```bash
bun add -g @th0rgal/ralph-wiggum
```

### From source (Linux/macOS)

```bash
git clone https://github.com/Th0rgal/open-ralph-wiggum
cd open-ralph-wiggum
./install.sh
```

### From source (Windows)

```powershell
git clone https://github.com/Th0rgal/open-ralph-wiggum
cd open-ralph-wiggum
.\install.ps1
```

---

## Quick Start

```bash
ralph "Build a REST API for todos with tests. Output <promise>COMPLETE</promise> when all tests pass." --max-iterations 20
```

Use `--agent claude-code`, `--agent codex`, `--agent copilot`, or `--agent cursor-agent` for other agents.

---

## Key Options

```
--agent AGENT            Agent to use (opencode|claude-code|codex|copilot|cursor-agent)
--model MODEL            Model name (agent-specific)
--max-iterations N       Stop after N iterations (always set as safety net)
--min-iterations N       Minimum iterations before completion (default: 1)
--completion-promise T   Text that signals completion (default: COMPLETE)
--tasks / -t             Enable Tasks Mode (structured multi-task tracking)
--prompt-file / -f PATH  Read prompt from file
--prompt-template PATH   Use custom Mustache-style template
--status                 Show live loop status from another terminal
--add-context TEXT       Inject hint mid-loop without stopping
--rotation LIST          Cycle through agent:model pairs each iteration
--no-questions           Disable interactive question handling
--allow-all              Auto-approve all permissions (default: on)
--no-plugins             Disable OpenCode plugins to avoid conflicts
```

---

## Monitoring

From a second terminal:

```bash
ralph --status              # Live dashboard
ralph --add-context "hint"  # Guide the agent
```

---

## When to Use

**Good for:** Tasks with automatic verification (tests passing, linter clean), well-defined scope, iterative refinement.

**Not good for:** Ambiguous requirements, architectural decisions, security-critical code, exploratory research.
