---
name: proactive-memory
description: Use when a user corrects you, shares a personal detail, teaches you something about their environment or preferences, or says "remember this". Also use when you discover a stable fact that will still matter in future sessions.
---

# Proactive Memory — Hermes-Style Memory Usage

Memory is durable storage for facts that shape future behavior. Use it proactively — don't wait to be asked.

## When to Save to Memory

| Trigger | Target | Example |
|---------|--------|---------|
| User corrects you | `human` | "Don't use direct Vercel deploys, push to GitHub instead" |
| User shares preference | `human` | "I prefer tabs over spaces" |
| User says "remember this" | `human` or `project` | Whatever they asked you to remember |
| You discover environment facts | `project` | "Project uses Poetry, not pip" |
| You learn a project convention | `project` | "Tests go in `tests/` with pytest" |
| Tool quirk discovered | `project` | "This tool needs `--no-cache` flag on Windows" |

## Priority Order

1. User preferences and corrections (most valuable — prevents repetition)
2. Environment facts (OS, tools, project structure)
3. Procedural knowledge (move to a skill if complex)

## What NOT to Save

- Task progress or session outcomes (that's what session history is for)
- Trivial/obvious info
- Things easily re-discovered
- Temporary TODO state
- Raw data dumps

## How to Use the Tools

```markdown
# Save a new fact
memory_set(label="human", value="- Prefers tabs over spaces", description="User preferences")

# Update an existing fact
memory_replace(label="human", oldText="- Prefers tabs over spaces", newText="- Prefers tabs over spaces for Python, spaces for JS")

# Check current memory
memory_list(scope="project")
```

## Rules

1. Save proactively after corrections — don't wait for the user to ask
2. Keep entries declarative and compact
3. One fact per entry
4. Remove stale entries when conventions change
5. If a procedure has multiple steps, create a skill instead of a memory entry
