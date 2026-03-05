# Project Instructions

This project follows the standard `ud:` command workflow. Run `/ud:next` to start.

## Project Context
<!-- Project-specific details: conventions, patterns, gotchas, environment setup.
     This is NOT for architecture (that's in PROJECT.md) or tasks (that's in .taskmaster/).
     This is for things the agent needs to know that aren't obvious from the code.
     Examples:
     - "We use Azure CLI for deployments, never Terraform"
     - "All API responses must include a correlation ID header"
     - "Tests run against a local Docker MongoDB, start with: docker compose up -d"
-->

## Default Role: Assisted
Start in **assisted mode** (`/ud:role-assisted`). Switch with `/ud:role-agentic` or `/ud:role-assisted`.
To change default, edit this line to `## Default Role: Agentic`.

## Completing a Task
1. Check for deviations — if implementation diverged from the task, explain why and run:
   `task-master update-task --from=<next_id> --prompt="<what changed and why>"`
2. Mark done — `task-master set-status --id=<id> --status=done`
3. Summarize — `##### Task <id>: <title>` + 2-3 sentence summary
4. Commit — ask before committing. Conventional commits: `feat:`, `fix:`, `docs:`, `chore:`, `refactor:`, `test:`. Ask before pushing.

## Git Conventions
- **`main`** is stable — never commit directly. Use `feature/<name>` branches.
- One branch per feature. Commit after each task via `/ud:done`.
