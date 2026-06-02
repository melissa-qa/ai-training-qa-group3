# QA Artifact Selection Prompts

Use these prompts to choose which QA artifacts to create or update for `automationexercise.com`.

## Prompt categories

- Artifact selection
- Template-based generation
- Update existing documents
- Clarifying assumptions and questions

## Suggested prompts

1. Create or update the QA strategy blueprint for `automationexercise.com` using only `docs/Requirements v1.md` and existing `docs/01-strategy` artifacts.
2. Generate a ranked risk matrix in `docs/01-strategy/risk-matrix.md` based on the site requirements and the highest-impact failure modes.
3. Define measurable quality gates for PR, nightly, and release in `docs/01-strategy/quality-gates.md`.
4. Build an assumptions and questions backlog in `docs/01-strategy/assumptions-and-questions.md` for missing information and test scope gaps.
5. Create a test plan in `docs/01-strategy/test-plan.md` aligned to the strategy blueprint and the documented requirements.
6. Draft two test cases in `docs/01-strategy/test-cases.md` using `docs/02-ai-operating-model/templates/test-case-template.md`.
7. Draft two bug reports in `docs/01-strategy/bug-report.md` using `docs/02-ai-operating-model/templates/bug-report-template.md`.
8. Review current `docs/01-strategy` files and recommend which artifacts need updating or completion.

## Prompt examples for repeated use

- “Which QA artifact should I create next for automationexercise.com, based on `docs/Requirements v1.md` and the existing strategy folder?”
- “Update the QA test plan and test cases for the highest-risk flows described in `docs/01-strategy/strategy-blueprint.md`.”
- “Create measurable quality gates and link them to `docs/01-strategy/risk-matrix.md`.”
- “Capture explicit assumptions and open questions for any missing test environment or data details.”

## How to use this file

1. Choose one or more prompts from this file.
2. Use the prompt text to instruct the QA artifact generation process.
3. Ensure the output is saved in `docs/01-strategy/` with the correct file name.
4. If the artifact already exists, update it with new information rather than replacing the file entirely.
