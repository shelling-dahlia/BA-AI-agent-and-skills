# BA AI Agent Skill Library

This project was created as a reusable business-analysis (BA) AI skill system for requirement discovery, decomposition, classification, and delivery support.

## Purpose
The system answers a practical question reliably: given a raw requirement, which artifact should be used and how should it be classified and validated?

This library adapts the modular structure and documentation discipline evident in the reference project while remaining reusable across projects rather than being fixed to a single product or domain.

## Scope
- Requirement clarification and elicitation
- Stakeholder and business objective analysis
- Feature, epic, user story, use case, task, and acceptance criteria classification
- Process and journey modelling support
- Traceability, prioritization, and change-impact analysis
- Validation and delivery planning

## Project structure
- `agents/ba-agent.md` — reusable BA agent definition and workflow
- `skills/` — focused BA skills with inputs, outputs, validation rules, and examples
- `templates/` — reusable BA artifacts and tracking files
- `standards/` — definitions, naming, quality gates, and traceability guidance
- `examples/ecommerce/` — end-to-end classification and traceability example
- `docs/ba-system-overview.md` — summary overview

## Source of truth and adaptation notes
- The reference project structure was used as a model for modularity and operating pattern.
- The classification logic is grounded in the BABOK and Agile Extension references reviewed in the attached core assessment and supporting materials.
- Terms are treated as conventions for this library rather than universal rules for every organization.
- Where the information is missing or ambiguous, the system records uncertainty and proposes a classification rather than inventing facts.

## Decision rule in one sentence
Raw requirements are clarified, grouped into business outcomes and constraints, then decomposed into features, epics, user stories or use cases, and implementation tasks, with acceptance criteria and traceability linking each item to a business outcome.

## Quick start
1. Read the BA agent definition in `agents/ba-agent.md`.
2. Select a skill from `skills/` based on the current work stage.
3. Use the templates in `templates/` to capture evidence.
4. Validate outputs with the standards in `standards/`.
5. Test the classification model with the e-commerce example in `examples/ecommerce/`.
