# Skill: Raw Requirement Analysis and Clarification

## Purpose
Turn a raw requirement into a structured requirement baseline with clarified scope, assumptions, constraints, and open questions.

## Input
- one or more raw requirement statements
- context, constraints, and known information
- stakeholder notes or examples

## Output
- requirement inventory
- clarified requirement statements
- assumptions, constraints, and unresolved questions
- candidate classification for each item

## Execution steps
1. Restate the requirement in neutral, concrete language.
2. Separate objective, constraint, assumption, question, and proposed feature.
3. Identify missing information and actor/value context.
4. Check whether the statement is a business need, a solution idea, or a specific requirement.
5. Label each output as `confirmed`, `proposal`, `assumption`, or `question`.
6. Recommend the next artifacts to create.

## Decision rules
- A need describes a business outcome.
- A requirement describes what must be true.
- A solution idea describes a way to deliver the need.
- A constraint limits the solution.
- An estimation or design note is not a requirement unless it is binding.

## Validation checks
- Is the statement understandable without implementation detail?
- Can the requirement be tested?
- Is it traceable to a business objective or stakeholder need?
- Is the statement free from unsupported assumptions?

## Example
Raw requirement: "Build an e-commerce website."

Refined analysis:
- Business objective: enable online selling and customer purchase journeys.
- Candidate requirements: product catalog, cart, checkout, account management, search, payments.
- Open questions: target audience, payment methods, shipping model, marketplace or single-seller model, compliance needs.
- Classification status: proposals until validated.
