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

MCP servers (`@upstash/context7-mcp`, `chrome-devtools-mcp`) auto-install via npx on first use.

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

### Custom skills (8) — under `config/skills/`

| Skill | Purpose |
|-------|---------|
| `open-ralph-wiggum` | Iterative AI coding loop |
| `claude-memory-kit` | Persistent memory with audit rituals |
| `chrome-extension-developer` | Chrome Extension Manifest V3 |
| `reverse-engineer` | Binary analysis / RE toolchain |
| `binary-analysis-patterns` | Compiled binary analysis |
| `file-organizer` | File/folder organization |
| `twitter-algorithm-optimizer` | Tweet optimization |
| `ui-ux-pro-max` | UI/UX design intelligence |

Plus 14 superpowers skills loaded by the `@obra/superpowers` plugin.

### Plugins & MCP

| Plugin/MCP | Source |
|------------|--------|
| `superpowers` | `github:obra/superpowers` |
| `opencode-agent-memory` | npm |
| `@ramarivera/opencode-model-announcer` | npm |
| `graphify.js` | custom plugin in `config/plugins/` |
| `context7-mcp` | `@upstash/context7-mcp@latest` (npx) |
| `chrome-devtools-mcp` | `chrome-devtools-mcp@latest` (npx) |

### Theme

`ayu-dark` — custom theme at `~/.config/opencode/themes/ayu-dark.json`

### Memory (persistent)

`~/.config/opencode/memory/` — `human.md`, `project.md`, `persona.md`

## Quick checklist

- [ ] OpenCode CLI installed (`opencode --version`)
- [ ] `config/` → `~/.config/opencode/`
- [ ] `npm install` in `~/.config/opencode/`

That's everything. 3 steps.
