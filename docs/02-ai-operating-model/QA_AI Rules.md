# QA_AI Rules

## Purpose
Provide reusable instructions for generating and updating QA artifacts for `automationexercise.com` in `docs/01-strategy`. This rule enforces that all QA outputs are derived only from `docs/Requirements v1.md` and existing strategy artifacts, without adding unapproved requirements.

## Scope
- Target application: `https://automationexercise.com/`
- Supported QA artifact outputs:
  - `docs/01-strategy/strategy-blueprint.md`
  - `docs/01-strategy/risk-matrix.md`
  - `docs/01-strategy/quality-gates.md`
  - `docs/01-strategy/assumptions-and-questions.md`
  - `docs/01-strategy/test-plan.md`
  - `docs/01-strategy/test-cases.md`
  - `docs/01-strategy/bug-report.md`
- Templates to use:
  - `docs/02-ai-operating-model/templates/test-case-template.md`
  - `docs/02-ai-operating-model/templates/bug-report-template.md`
- Prompt selection helper:
  - `docs/02-ai-operating-model/prompt-library/qa-artifact-selection-prompts.md`

## Rules
1. Do not add requirements that are not present in `docs/Requirements v1.md`.
2. If an idea is outside the documented requirements, capture it only as a question or an assumption in `assumptions-and-questions.md`.
3. Use tables where possible. If tables are not appropriate, use bold section titles and numbered sublists.
4. Keep `strategy-blueprint.md` to 1–2 pages maximum.
5. Always reference the source of scope and constraints as `docs/Requirements v1.md` or the existing `docs/01-strategy` artifacts.
6. Use the prompt library file to choose which artifacts need creation or update.
7. Preserve existing artifacts and update them when asked, rather than replacing them without context.

## Artifact generation workflow

### 1. Review inputs
- Read `docs/Requirements v1.md` thoroughly.
- Review the existing files in `docs/01-strategy/`.
- Review test and bug templates in `docs/02-ai-operating-model/templates/`.

### 2. Select artifacts
- Use `docs/02-ai-operating-model/prompt-library/qa-artifact-selection-prompts.md` to choose the artifacts that need creation or update.
- When selecting artifacts, consider whether the output should be a new document or an update of an existing file.

### 3. Produce outputs
- `strategy-blueprint.md`
  - Include: scope and scope boundaries; test approach by layer (UI/API/E2E) aligned to risk; environment and minimal test data strategy; measurable exit criteria; roles and responsibilities.
  - Mention automation tools: Playwright + .NET for UI/API/E2E and JMeter for performance.
  - Keep it within 1–2 pages.
- `risk-matrix.md`
  - Create a ranked risk matrix of 8–12 risks.
  - Include module, risk, impact rationale, probability, coverage definition, and affected quality gate.
  - Rank by high impact first, then high probability.
- `quality-gates.md`
  - Define measurable gates for Pull Request, Nightly, and Release.
  - Include pass criteria, scope, and evidence required.
- `assumptions-and-questions.md`
  - Capture explicit assumptions rooted in missing information.
  - Include actionable clarifying questions for product, development, security, or operations.
- `test-plan.md`
  - Use the existing strategy blueprint as the basis.
  - Recommend a test plan aligned to the scope, risk, and layers.
- `test-cases.md`
  - Use 2 requirements from the existing artifacts and the test-case template.
  - Provide two concrete test cases with preconditions, steps, data, expected results, and execution metadata.
- `bug-report.md`
  - Identify 2 actual bugs against `automationexercise.com`.
  - Use the bug-report template and provide enough detail for reproduction and triage.

### 4. Validate outputs
- Confirm each artifact is traceable to `Requirements v1.md`.
- Confirm no new requirements are introduced as assumed facts.
- Confirm the artifact names and locations match the rules above.

## Artifact-specific guidance

### Strategy blueprint
- Use exact wording such as “included” and “out of scope.”
- Align test approach to risk and automation tooling.
- Include measurable metrics for exit criteria, for example:
  - `100% smoke tests passed`
  - `95th percentile API latency < 200ms`
  - `≤ 15% deviation on automated tests`

### Risk matrix
- Rank risks instead of simply listing them.
- Make each risk description compact and tied to user-facing or system-level impact.
- Explicitly state what coverage means for each risk.

### Quality gates
- Make gate definitions measurable and actionable.
- Include specific pass/fail thresholds.
- Include evidence items for each gate.

### Assumptions and questions
- Keep assumptions explicit and minimal.
- Convert any undocumented suggestion into a question when possible.
- Organize questions into categories such as Environments, Test Data, API, Performance, and Accessibility.

### Test plan, test cases, and bug report
- Use the templates in `docs/02-ai-operating-model/templates/`.
- Respect the requested artifact structure and naming.
- Prefer two concrete examples for requirements and two bug reports with real reproduction details.

## Reuse guidance
- If asked to generate new artifacts later, follow this same rule set.
- When updating existing artifacts, preserve the original structure and clearly state what changed.
- Use the prompt library as the decision point for artifact selection.

## Suggested prompt usage
- When preparing work, use prompts from `docs/02-ai-operating-model/prompt-library/qa-artifact-selection-prompts.md`.
- Example prompt: “Select the QA artifact(s) to create or update for automationexercise.com based only on `Requirements v1.md` and existing `docs/01-strategy` artifacts.”

## Important constraint
Any suggestion that is not already covered in `Requirements v1.md` must be captured as an assumption or a clarifying question, never as a new functional requirement.
