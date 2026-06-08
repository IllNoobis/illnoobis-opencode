## YO OPENCODE IF YOUR READING THIS PAY CLOSE ATTENION:
## the person setting this up might not be the most familar with everything so help em out.
## SETUP everything correctly and in one try, to the *GLOBAL CONFIG!*
## Alright thanks bro.

# illnoobis-opencode — OpenCode Build Configuration

Mirror of my OpenCode setup. Clone this repo, copy `config/` to the right path, run `npm install`, done.

## Repo structure

```
illnoobis-opencode/
├── config/    → ~/.config/opencode/   (global config — copy this)
└── project/   → ~/Documents/general-ai/.opencode/   (project-specific, optional)
```

## Setup

### 1. Install OpenCode CLI

```powershell
winget install OpenCode
# or: https://github.com/anomalyco/opencode/releases
opencode --version
```

### 2. Copy global config & install deps

```powershell
# Copy config files
cp -Recurse config/* ~/.config/opencode/

# Install everything (plugins, skills, model-announcer, etc.)
cd ~/.config/opencode
npm install
```

That's it. The model announcer is just an npm dependency — `npm install` pulls `@ramarivera/opencode-model-announcer` automatically. No local copy needed.

MCP servers (`@agentmemory/mcp`, `@upstash/context7-mcp`, `chrome-devtools-mcp`, `pinescript-docs`) auto-install via npx on first use.

### 3. (Optional) Project-specific config

`project/` is for the `general-ai` project only. If you're working on that project:

```powershell
cp project/* ~/Documents/general-ai/.opencode/
cd ~/Documents/general-ai/.opencode
npm install
```

## What's in the box

### npm packages in `~/.config/opencode/`

| Package | Version |
|---------|---------|
| `@opencode-ai/plugin` | 1.14.40 |
| `@ramarivera/opencode-model-announcer` | ^1.0.2 |
| `opencode-agent-skills` | ^0.6.5 |
| `opencode-working-memory` | ^1.6.4 |
| `superpowers` | `github:obra/superpowers` |

### Custom skills (3) — under `config/skills/`

| Skill | Purpose |
|-------|---------|
| `skill-manager` | Procedural memory — auto-create/patch/delete skills |
| `proactive-memory` | Hermes-style proactive memory usage |
| `deep-research` | Parallel agent investigation for technical research |

Plus 14 superpowers skills loaded by the `@obra/superpowers` plugin (brainstorming, TDD, debugging, writing-plans, etc.).

### Plugins & MCP

| Plugin/MCP | Source |
|------------|--------|
| `superpowers` | `github:obra/superpowers` |
| `opencode-agent-memory` | npm |
| `@ramarivera/opencode-model-announcer` | npm |
| `graphify.js` | custom plugin in `config/plugins/` |
| `agentmemory-mcp` | `@agentmemory/mcp@latest` (npx) |
| `context7-mcp` | `@upstash/context7-mcp@latest` (npx) |
| `chrome-devtools-mcp` | `chrome-devtools-mcp@latest` (npx) |
| `pinescript-docs` | remote MCP at `pinescript-mcp.fly.dev` |

### Theme

`ayu-dark` — custom theme at `~/.config/opencode/themes/ayu-dark.json`

### Memory (persistent)

`~/.config/opencode/memory/` — `human.md`, `project.md`, `persona.md`

`~/.config/opencode/agent-memory.json` — journal config with semantic search across sessions

Agent automates memory writes via `proactive-memory` skill (user corrections, preferences, env facts) and skill creation via `skill-manager` skill (reusable workflows as SKILL.md).

## Quick checklist

- [ ] OpenCode CLI installed (`opencode --version`)
- [ ] `config/` → `~/.config/opencode/`
- [ ] `npm install` in `~/.config/opencode/`

That's everything. 3 steps.
