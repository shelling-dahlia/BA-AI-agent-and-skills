# Skill: Use Case Identification and Specification

## Purpose
Describe how actors interact with the solution to achieve a goal, including the main and alternative paths.

## Input
- actor and goal context
- process or workflow notes
- feature or capability boundary

## Output
- use case catalogue
- primary and secondary actors
- preconditions, triggers, flows, post-conditions
- include/extend relationships if relevant

## Execution steps
1. Define the actor and goal.
2. Write the use case from the actor viewpoint.
3. Separate main, alternative, and exception flows.
4. Ensure post-conditions hold for every flow.
5. Link business rules to the correct requirement rather than embedding them in the use case.

## Rules
- Use cases describe user/system interaction, not internal design.
- A single use case has one clear goal.
- Business rules and UI detail should be handled in their own artifacts when more appropriate.

## Validation checks
- A trigger and successful outcome are clear.
- Main flow is distinct from alternate and exception flows.
- The use case is actor-centric and not solution-design-heavy.
