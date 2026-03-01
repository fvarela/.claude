# Generate PRD

Use the **prd-taskmaster** skill to generate a Product Requirements Document.

Check if `.claude/docs/INPUT.md` exists and has content. If it does, use it as the input for PRD generation.
If `INPUT.md` is empty or missing, and $ARGUMENTS is provided, use that instead.
If neither exists, ask the user what feature or product they want a PRD for.
