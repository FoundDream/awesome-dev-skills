---
name: commit
description: Git commit helper for multi-agent collaboration. Use this skill when committing changes in a shared workspace where multiple agents work simultaneously. Ensures clean, focused commits by only staging files YOU modified, avoiding conflicts with other agents' work.
---

# Multi-Agent Git Commit

When multiple agents work in the same repository, each agent must commit only its own changes to maintain clear history and avoid conflicts.

## Commit Workflow

1. **Check current status**

   ```bash
   git status
   ```

2. **Review your changes**

   ```bash
   git diff
   ```

3. **Stage ONLY files you modified** - Never use `git add .` or `git add -A`

   ```bash
   git add <specific-file-1> <specific-file-2>
   ```

4. **Verify staged changes are yours**

   ```bash
   git diff --staged
   ```

5. **Commit with descriptive message**

   ```bash
   git commit -m "$(cat <<'EOF'
   <type>: <description>

   Co-Authored-By: Claude <noreply@anthropic.com>
   EOF
   )"
   ```

## Rules

- **Never** use `git add .`, `git add -A`, or `git add --all`
- **Always** stage files individually by name
- **Skip** files you did not create or modify
- **Verify** staged changes before committing
- **Keep** commits focused on a single logical change

## Commit Message Format

```
<type>: <short description>

[optional body explaining why]

Co-Authored-By: Claude <noreply@anthropic.com>
```

Types: `feat`, `fix`, `refactor`, `docs`, `test`, `chore`, `style`
