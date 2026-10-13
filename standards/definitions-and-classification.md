# Definitions and Classification Framework

## Purpose
Provide a reusable decision framework for distinguishing business need, requirement, capability, feature, epic, user story, use case, task, and acceptance criterion.

## Core definitions
- Business need: a problem, opportunity, or outcome that motivates action.
- Requirement: a statement of what the solution must provide or satisfy.
- Capability or feature: a cohesive set of requirements delivering value.
- Epic: a large chunk of value that can be decomposed into smaller items.
- User story: a short statement of value to a stakeholder, usually supported by acceptance criteria.
- Use case: a goal-oriented interaction between actor and solution.
- Task: an implementation or delivery unit required to produce the outcome.
- Acceptance criterion: an objective test to confirm the item meets the need.
- Assumption: something accepted as true for planning but not yet confirmed.
- Constraint: a limit or rule that shapes solution design.
- Risk: uncertainty or threat affecting the initiative.
- Unresolved question: a fact or decision still pending.

## Comparison matrix

| Artifact | Purpose | Typical level | Key evidence | Typical check |
|---|---|---:|---|---|
| Business need | Why the work matters | Strategic | outcome, pain, value | Is there a real problem or opportunity? |
| Requirement | What must be true | Business/solution | statement, source, trace | Is it testable and specific? |
| Feature | Cohesive set of value | Solution | value grouping | Is it cohesive and valuable? |
| Epic | Large value chunk | Portfolio/release | grouping of stories | Can it be decomposed? |
| User story | What for whom and why | Delivery | role, behaviour, value | Does it meet INVEST and acceptance criteria? |
| Use case | How the goal is achieved | Functional behaviour | actor, trigger, flows | Is there one clear goal and outcome? |
| Task | How we implement | Delivery/execution | work breakdown | Is it decomposed and sequenced? |
| Acceptance criterion | What proves it works | Validation | pass/fail condition | Is it objective and testable? |

## Decision tree
1. Is the statement about the problem, opportunity, or reason for change? -> Business need or objective.
2. Is it a required behaviour or condition? -> Requirement.
3. Is it a cohesive bundle of related requirements with value to stakeholders? -> Feature.
4. Is it a large value chunk for release planning? -> Epic.
5. Is it a stakeholder-valued slice with a clear benefit? -> User story.
6. Is it an actor-to-solution interaction with a goal and flows? -> Use case.
7. Is it a work item for implementation? -> Task.
8. Is it a pass/fail condition? -> Acceptance criterion.

## Common mistakes
- Treating stories, features, and use cases as synonyms.
- Writing implementation tasks as if they were requirements.
- Hiding uncertainty under a “confirmed” label.
- Creating acceptance criteria that are subjective or non-testable.

## System convention
This library adopts the convention that business outcomes remain the anchor; feature, story, and use case are complementary views rather than interchangeable replacements. A project can tailor the naming, but the distinction should stay visible.
