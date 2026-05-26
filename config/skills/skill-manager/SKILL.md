---
name: skill-manager
description: Use when you have discovered a reusable workflow, solved a non-trivial problem, been corrected on a procedure, or the user asks you to save an approach for future reuse. Also use to patch/edit/delete existing skills when instructions become stale or you find missing steps.
---

# Skill Manager — Procedural Memory

Skills are your procedural memory. Save any reusable workflow, non-trivial command sequence, or corrected approach as a skill so future sessions benefit from past effort.

## When to Create a Skill

- Complex task succeeded (5+ tool calls)
- You overcame errors or obstacles with a specific approach
- User corrected your approach and the correction is reusable
- You discovered a non-trivial workflow or command sequence
- User explicitly asks "remember this for next time"

## When to Patch a Skill

- Instructions are stale or wrong
- OS-specific failures not covered
- Missing steps or pitfalls found during use
- A better approach was discovered

## Skill Directory Structure

Skills live in the first found location:
- Project: `.opencode/skills/<name>/SKILL.md`
- Global: `~/.config/opencode/skills/<name>/SKILL.md`

## How to Create a Skill

1. Use `Read` to check if a skill with this name already exists
2. Use `Write` to create `<skill-dir>/SKILL.md` with YAML frontmatter
3. Verify the name is lowercase with hyphens, max 64 chars

### Skill Format

```markdown
---
name: my-skill-name
description: Use when [specific triggering conditions]
---

# My Skill Name

## Overview
What this skill does in 1-2 sentences.

## When to Use
- Trigger 1
- Trigger 2

## Steps
1. Step one
2. Step two

## Common Pitfalls
- What goes wrong
- How to fix it

## Verification
How to confirm success
```

## How to Patch a Skill

1. `Read` the existing SKILL.md
2. Use `Edit` with the exact old/new string match
3. Verify the frontmatter is still valid

## How to Delete a Skill

Use `Bash` with `Remove-Item` to delete the skill directory when it's no longer relevant.

## Rules

1. Always ask the user before creating or deleting a skill — skills affect future sessions
2. After a difficult/iterative task, offer to save the approach as a skill
3. Patch skills immediately when you hit issues not covered by them
4. Skip saving trivial one-off commands
5. After any skill write, prompt: "Run `opencode` in a new session to verify the skill loads correctly"
