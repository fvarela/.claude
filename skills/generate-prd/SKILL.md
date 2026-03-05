---
name: generate-prd
description: >-
  Generate a Product Requirements Document from PROJECT.md. Use when user says
  "new PRD", "generate PRD", or runs /ud:new-prd. Reads PROJECT.md for project context,
  checks existing PRDs in .taskmaster/docs/ to determine the next phase, and generates
  a focused PRD ready for /ud:parse-prd. No API key needed.
allowed-tools:
  - Read
  - Write
  - Edit
  - Glob
  - Bash
  - AskUserQuestion
---

# Generate PRD from PROJECT.md

You are generating a Product Requirements Document for the next phase/feature of a project.
This skill replaces the external prd-taskmaster skill with a simpler, PROJECT.md-driven approach.

## Step 1: Read PROJECT.md

Look for `PROJECT.md` in the project root.

If it doesn't exist, tell the user:
> "No PROJECT.md found. Run `/ud:init` to set up the project structure, then fill in PROJECT.md before generating a PRD."

Stop here if PROJECT.md is missing.

## Step 2: Identify the next phase

Look for the **Development Phases** section in PROJECT.md. It contains a checkbox list like:

```
- [x] Phase 1: Project scaffolding and CI/CD setup
- [x] Phase 2: Core data model and storage layer
- [ ] Phase 3: API endpoints and authentication
- [ ] Phase 4: Background job processing
```

Find the **first unchecked phase** — that's the next one to generate a PRD for.

If the Development Phases section is missing or empty:
- Check `.taskmaster/docs/` for existing PRD files
- Check `.taskmaster/tasks/tasks.json` for existing tasks and their statuses
- Based on the modules and their statuses in PROJECT.md, infer what the next logical work is
- Present your assessment and ask the user to confirm

If a Development Phases section exists and has a clear next phase, present it:
> "The next phase is: **Phase 3: API endpoints and authentication**.
> Should I generate a PRD for this, or do you want a different one?"

Wait for confirmation before generating.

## Step 3: Gather context for the PRD

From PROJECT.md, read and use:
- **Overview** — to understand the project's purpose and frame the PRD
- **Architecture** — to reference components, infrastructure, and how things connect
- **Modules** — to identify which modules are involved in this phase and their tech stack
- **Design Principles** — to ensure the PRD aligns with project principles
- **Decisions** — to reference relevant past decisions

Also check `.claude/docs/INSTRUCTIONS.md` for project-specific conventions.

## Step 4: Generate the PRD

Write a PRD with this structure:

```markdown
# PRD: [Phase Name from Development Phases]

**Author:** Developer
**Date:** [today's date]
**Status:** Draft
**Source:** PROJECT.md — [Phase reference]

---

## Summary

[2-3 sentences: what this phase accomplishes and why it matters]

## Problem Statement

[What problem does this phase solve? What's the current state?]

## Goals

- [Concrete, measurable goal 1]
- [Concrete, measurable goal 2]
- ...

## Requirements

### Must Have

1. **[REQ-001]**: [Requirement title]
   - Description: [what it does]
   - Acceptance: [how to verify it's done]

2. **[REQ-002]**: ...

### Should Have

[Lower priority requirements]

### Out of Scope

[Explicitly list what this phase does NOT cover — reference future phases]

## Technical Notes

[Architecture decisions, file locations, patterns to follow, dependencies.
Pull from PROJECT.md's Architecture, Modules, and Design Principles sections.
Reference conventions from .claude/docs/INSTRUCTIONS.md if available.]

## Task Breakdown Hints

[Suggest a rough ordering of work. This helps /ud:parse-prd generate better tasks.]

1. [First thing to build] - depends on nothing
2. [Second thing] - depends on 1
3. ...
```

## Step 5: Write the PRD

Save to `.taskmaster/docs/<phase-name>-requirements.md`.

Derive the filename from the phase name in kebab-case.
Example: "Phase 3: API endpoints and authentication" → `phase3-api-endpoints-auth-requirements.md`

If `.taskmaster/docs/` doesn't exist, create it.

## Step 6: Next steps

Tell the user:
> "PRD saved to `.taskmaster/docs/<filename>`.
> Review it, then run `/ud:parse-prd` to generate tasks.
> After completing this phase, mark it done in PROJECT.md's Development Phases section."

## PRD Quality Rules

- **Be specific**: "Implement OAuth2 with GitHub provider" not "Add authentication"
- **Reference PROJECT.md**: Pull tech stack, architecture, conventions, testing strategy directly
- **Size appropriately**: A PRD should generate 5-15 tasks. If it would generate more, suggest splitting the phase in PROJECT.md.
- **Include acceptance criteria**: Every requirement needs a concrete "how to verify" statement
- **Stay in scope**: Only cover what the phase describes. Reference future phases in Out of Scope.
- **Use the project's language**: If PROJECT.md says "MongoDB", don't say "database". Be specific.
