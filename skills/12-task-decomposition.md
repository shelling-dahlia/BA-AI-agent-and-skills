# Skill: Task Decomposition and Dependency Identification

## Purpose
Break a story or feature into implementation tasks while preserving dependency clarity and readiness for execution.

## Input
- accepted story or feature
- delivery team context
- known architecture or technical constraints

## Output
- technical or delivery task list
- dependency map
- sequencing and ownership notes
- estimate assumptions

## Execution steps
1. Identify the smallest meaningful unit of work.
2. Separate work by system component or team area only when needed.
3. Capture dependencies: prerequisite, blocked-by, parallelizable, or external waiting.
4. Sequence tasks based on critical path and risk.
5. Mark assumptions and open design items.

## Rules
- Task decomposition is not equivalent to requirement decomposition.
- Tasks should support delivery, not redefine the user need.
- Keep dependencies explicit and reviewable.

## Validation checks
- Are tasks sufficiently granular for execution?
- Are dependencies realistic and visible?
- Is the output linked to the story or feature being delivered?
