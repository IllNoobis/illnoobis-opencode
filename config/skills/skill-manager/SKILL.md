---
name: skill-manager
description: Use when you have discovered a reusable workflow, solved a non-trivial problem, been corrected on a procedure, or the user asks you to save an approach for future reuse. Also use to patch/edit/delete existing skills when instructions become stale or you find missing steps.
---

# Skill Manager — Procedural Memory

Skills are your procedural memory. Save any reusable workflow, non-trivial command sequence, or corrected approach as a skill so future sessions benefit from past effort.

## When to Create a Skill

- Complex task succeeded (5+ tool calls with a consistent pattern)
- You overcame errors or obstacles with a specific approach
- User corrected your approach and the correction is reusable
- You discovered a non-trivial workflow or command sequence
- User explicitly asks "remember this for next time"
- You wrote a multi-step plan that could apply to future similar tasks

## When NOT to Create a Skill

- One-off commands (just save to memory)
- Session-specific debugging that won't repeat
- General knowledge better stored in memory
- Trivial workflows (1-2 steps, no pitfalls)

## When to Patch a Skill

- Instructions are stale or wrong after tool/API updates
- OS-specific failures not covered
- Missing steps or pitfalls found during use
- A better approach was discovered
- User reports the skill didn't help or was misleading

## Skill Quality Checklist

Before creating a skill, verify:
- [ ] Name is lowercase-kebab-case, max 64 chars, self-explanatory
- [ ] Description in frontmatter is trigger-based ("Use when...") not summary-based
- [ ] Has a "When to Use" section with specific triggers
- [ ] Has numbered steps in logical order
- [ ] Has "Common Pitfalls" section with real gotchas
- [ ] Has "Verification" section showing how to confirm success
- [ ] Is focused on ONE workflow (don't combine multiple patterns)

## Skill Directory Structure

Skills live in the first found location:
- Project: `.opencode/skills/<name>/SKILL.md`
- Global: `~/.config/opencode/skills/<name>/SKILL.md`

## How to Create a Skill

1. `Read` the existing skill-manager and proactive-memory skills to stay current
2. Use `Read` to check if a skill with this name already exists
3. Use `Write` to create `<skill-dir>/SKILL.md` with YAML frontmatter
4. Name is lowercase with hyphens, max 64 chars, describes what it does

### Skill Template

```markdown
---
name: my-skill-name
description: Use when [specific triggering condition] — NOT a general summary
---

# My Skill Name

## Overview
1-2 sentences. What problem does this solve? When is it the right tool?

## When to Use
- Specific trigger 1: "deploy to production", "add a new API route"
- Specific trigger 2: "fix CORS error", "set up auth"
- avoid vague triggers like "when asked to code"

## Prerequisites
- What tools/packages need to be installed
- What environment variables must be set
- What prior steps must have been completed

## Steps
1. Step one with exact commands
2. Step two with expected output checks
3. Step three

## Example
A concrete example with real paths/names (not placeholders).

## Common Pitfalls
- What goes wrong and how to detect it early
- Exact error messages to watch for
- How to fix each pitfall

## Verification
- How to confirm success (exact command + expected output)
- What "done" looks like
```

## How to Patch a Skill

1. `Read` the existing SKILL.md
2. Use `Edit` with the exact old/new string match
3. Verify the frontmatter is still valid
4. Add a note at the bottom: `Last patched: <date> - <reason>`

## How to Delete a Skill

Use `Bash` with `Remove-Item` to delete the skill directory when it's no longer relevant.

## Rules

1. Always ask the user before creating or deleting a skill — skills affect future sessions
2. After a difficult/iterative task, offer to save the approach as a skill
3. Patch skills immediately when you hit issues not covered by them
4. Skip saving trivial one-off commands
5. After any skill write, prompt: "Run `opencode` in a new session to verify the skill loads correctly"
6. Frontmatter `description` must be trigger-based ("Use when X happens") — not a summary of what the skill does
7. Include concrete examples with real paths, real commands, real error messages — avoid placeholders
8. Skills should be testable: include a verification step that produces observable output
