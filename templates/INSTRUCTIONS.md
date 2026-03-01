# Development Workflow

## Project Context
<!-- Replace this section with project-specific details: tech stack, architecture,
     conventions, deployment targets, or anything the agent needs to know. -->

## Default Role: Assisted
Start in **assisted mode** (`/ud:role-assisted`). Switch with `/ud:role-agentic` or `/ud:role-assisted`.
To change default, edit this line to `## Default Role: Agentic`.

## Task Management
This project uses Task Master. Tasks: `.taskmaster/tasks/tasks.json`.

### Completing a Task
1. **Check for deviations** — compare implementation against task description. If deviated, explain it and run:
   `task-master update-task --from=<next_id> --prompt="<what changed and why>"`
2. **Mark done** — `task-master set-status --id=<id> --status=done`
3. **Summarize** — print: `##### Task <id>: <title>` + 2-3 sentence summary
4. **Commit** — ask user before committing. Use conventional commits (`feat:`, `fix:`, `docs:`, `chore:`, `refactor:`, `test:`). Ask again before pushing.

## Git Conventions
- **`main`** is stable — never commit directly. Use `feature/<n>` branches.
- One branch per feature. Commit after each task via `/ud:done`.
- When feature is complete, merge to main and delete the branch.
