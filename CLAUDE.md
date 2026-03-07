# Project-Specific Instructions
Read the following files if they exist:
- `.claude/docs/INSTRUCTIONS.md` — Development workflow and task completion protocol

# Tool Usage Rules
- **NEVER use Glob to check if a file exists.** Always use `ls <path>` or `cat <path>` via Bash instead. Glob is broken for `.claude/` paths and returns false negatives.
- To check file existence: `ls .claude/docs/INSTRUCTIONS.md` — NOT `Glob ".claude/docs/INSTRUCTIONS.md"`
