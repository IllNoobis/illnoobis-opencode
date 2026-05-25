# general-ai — OpenCode Build Setup

This document lists everything needed to replicate this OpenCode build on another Windows machine.

## 1. Install OpenCode CLI

```powershell
winget install OpenCode
# or download from https://github.com/anomalyco/opencode/releases
```

Verify version (this build uses **v1.15.10**):
```powershell
opencode --version
```

## 2. Dependencies (npm packages)

Run these in each `.opencode/` directory to install plugins:

### Global config (`%USERPROFILE%\.config\opencode\`)
```powershell
cd ~\.config\opencode
npm install
```
Packages installed:
- `@opencode-ai/plugin@1.14.40`
- `@ramarivera/opencode-model-announcer@^1.0.2`
- `opencode-agent-skills@^0.6.5`
- `opencode-working-memory@^1.6.4`
- `superpowers@github:obra/superpowers`

### Legacy local config (`%USERPROFILE%\.opencode\`)
```powershell
cd ~\.opencode
npm install
```
Packages installed:
- `@opencode-ai/plugin@1.14.40`
- `opencode-working-memory@^1.6.4`

### Project-level config (`%USERPROFILE%\Documents\general-ai\.opencode\`)
```powershell
cd %USERPROFILE%\Documents\general-ai\.opencode
npm install
```
Packages installed:
- `@opencode-ai/plugin@1.15.7`

### Model announcer (custom)
```powershell
cd ~\opencode-model-announcer
npm install
```

## 3. MCP Servers (auto-installed on use via npx)

These are configured in `~\.config\opencode\opencode.jsonc` and install on first use:

```powershell
npx -y @upstash/context7-mcp@latest
npx -y chrome-devtools-mcp@latest
```

## 4. Copy these directories/files

| Source | Destination | Description |
|--------|-------------|-------------|
| `~\.config\opencode\` | same path | **Global config** — main config, plugins, memory, theme, MCP setup |
| `~\.opencode\skills\` | same path | **Custom skills** (8 skills installed) |
| `~\.opencode\plugins\graphify.js` | same path | Graphify plugin |
| `~\.opencode\tui.json` | same path | TUI layout config |
| `~\.opencode\memory\` | same path | Memory files |
| `~\opencode-model-announcer\` | same path | Custom model announcer package |
| `~\AGENTS.md` | same path | Agent instructions with graphify setup |
| `~\Documents\general-ai\` | same path | **This project folder** + project-level `.opencode\` config |

## 5. Custom skills installed

Located at `~\.opencode\skills\`:

| Skill | Description |
|-------|-------------|
| `open-ralph-wiggum` | Iterative AI coding loop agent |
| `claude-memory-kit` | Persistent memory with audit rituals |
| `chrome-extension-developer` | Chrome Extension Manifest V3 |
| `reverse-engineer` | Binary analysis / RE toolchain |
| `binary-analysis-patterns` | Compiled binary analysis |
| `file-organizer` | File/folder organization |
| `twitter-algorithm-optimizer` | Tweet optimization |
| `ui-ux-pro-max` | UI/UX design intelligence |

Plus **14 built-in superpowers skills** (from `@obra/superpowers`) loaded via the global config plugin.

## 6. Theme

- Custom theme: `ayu-dark` (saved at `~\.config\opencode\themes\ayu-dark.json`)

## 7. Quick checklist

- [ ] OpenCode CLI v1.15.10+ installed (`opencode --version`)
- [ ] `npm install` run in `~\.config\opencode\`
- [ ] `npm install` run in `~\.opencode\`
- [ ] `npm install` run in `~\Documents\general-ai\.opencode\`
- [ ] `~\.config\opencode\` fully copied
- [ ] `~\.opencode\skills\` fully copied
- [ ] `~\.opencode\plugins\graphify.js` copied
- [ ] `~\.opencode\tui.json` copied
- [ ] `~\AGENTS.md` copied
- [ ] `~\opencode-model-announcer\` copied + `npm install`
- [ ] `~\Documents\general-ai\` fully copied
