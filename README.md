# illnoobis-opencode — OpenCode Build Configuration

Mirror of my OpenCode setup. Clone this repo, copy files to the right paths, run `npm install`, and you're good.

## Repo structure

```
illnoobis-opencode/
├── config/              → ~/.config/opencode/          (global config)
├── project/             → ~/Documents/general-ai/.opencode/  (project plugins)
└── model-announcer/     → ~/opencode-model-announcer/  (plugin source)
```

## Setup steps

### 1. Install OpenCode CLI

```powershell
winget install OpenCode
# or: https://github.com/anomalyco/opencode/releases
opencode --version
```

### 2. Copy files

```powershell
# Global config
cp -Recurse config/* ~/.config/opencode/

# Project-level config
cp project/* ~/Documents/general-ai/.opencode/

# Model announcer plugin
cp -Recurse model-announcer ~/opencode-model-announcer
```

### 3. Install npm dependencies

```powershell
cd ~/.config/opencode && npm install
cd ~/Documents/general-ai/.opencode && npm install
cd ~/opencode-model-announcer && npm install
```

MCP servers (`@upstash/context7-mcp`, `chrome-devtools-mcp`) auto-install via npx on first use — no extra step.

### 4. Installed packages

| Location | Packages |
|----------|----------|
| `~/.config/opencode/` | `@opencode-ai/plugin@1.14.40`, `@ramarivera/opencode-model-announcer@^1.0.2`, `opencode-agent-skills@^0.6.5`, `opencode-working-memory@^1.6.4`, `superpowers@github:obra/superpowers` |
| `project/` | `@opencode-ai/plugin@1.15.7` |
| `model-announcer/` | `@opencode-ai/plugin@1.1.18` |

### 5. Custom skills (8)

Installed under `~/.config/opencode/skills/`:

| Skill | Purpose |
|-------|---------|
| `open-ralph-wiggum` | Iterative AI coding loop |
| `claude-memory-kit` | Persistent memory with audit rituals |
| `chrome-extension-developer` | Chrome Extension Manifest V3 |
| `reverse-engineer` | Binary analysis / RE toolchain |
| `binary-analysis-patterns` | Compiled binary analysis |
| `file-organizer` | File/folder organization |
| `twitter-algorithm-optimizer` | Tweet optimization |
| `ui-ux-pro-max` | UI/UX design intelligence (with data + scripts) |

Plus 14 superpowers skills loaded by the `@obra/superpowers` plugin.

### 6. Plugins & MCP

| Plugin/MCP | Source |
|------------|--------|
| `superpowers` | `github:obra/superpowers` |
| `opencode-agent-memory` | npm |
| `@ramarivera/opencode-model-announcer` | npm (local copy in `model-announcer/`) |
| `graphify.js` | custom plugin in `config/plugins/` |
| `context7-mcp` | `@upstash/context7-mcp@latest` (npx) |
| `chrome-devtools-mcp` | `chrome-devtools-mcp@latest` (npx) |

### 7. Theme

`ayu-dark` — custom theme at `~/.config/opencode/themes/ayu-dark.json`

### 8. Quick checklist

- [ ] OpenCode CLI installed (`opencode --version`)
- [ ] `config/` → `~/.config/opencode/`
- [ ] `npm install` in `~/.config/opencode/`
- [ ] `project/` → `~/Documents/general-ai/.opencode/`
- [ ] `npm install` in `~/Documents/general-ai/.opencode/`
- [ ] `model-announcer/` → `~/opencode-model-announcer/`
- [ ] `npm install` in `~/opencode-model-announcer/`
