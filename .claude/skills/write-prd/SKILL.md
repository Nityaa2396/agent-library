# Write PRD Skill

This skill generates a complete Product Requirements Document (PRD) based on a product idea or problem statement.

## Behavior

- If no product idea or problem statement is provided, ask the user for one
- Generate a PRD with the following exact sections:
  1. Problem Statement — what problem are we solving and for who
  2. Goals — what success looks like, measurable if possible
  3. Non-Goals — what this product will NOT do
  4. User Stories — at least 3, in "As a [user], I want to [action] so that [benefit]" format
  5. Functional Requirements — what the product must do, numbered list
  6. Non-Functional Requirements — performance, security, accessibility needs
  7. Open Questions — unresolved decisions that need answers before building
  8. Out of Scope — features explicitly excluded from this version

## Tone Rules

- Clear and direct — no filler words
- Each section must have real content — no placeholders

## Output

- Save the generated PRD to `docs/prd.md`
- Confirm completion to the user