# Test Plan: automationexercise.com QA

## Purpose
This test plan defines the execution approach for validating `automationexercise.com` based on `docs/Requirements v1.md` and the existing strategy blueprint. It supports UI, API, E2E, and performance testing across the site’s core user flows.

## Scope
- Included:
  1. Homepage and header navigation links.
  2. Product catalog display, category/brand filter navigation, and search functionality.
  3. Shopping cart actions: add item, remove item, update quantity, and checkout flow.
  4. User management: registration, login, duplicate-email validation, and logout.
  5. `/api_list` API contract validation for product, user, cart, and order endpoints.
  6. Responsive UI checks for Desktop, Tablet, and Mobile widths.
  7. Performance targets for page load and API latency.
- Out of scope:
  1. Real payment gateway integrations beyond the dummy payment handling in the checkout flow.
  2. Admin interfaces or internal tooling not referenced in `Requirements v1.md`.
  3. Security penetration testing beyond functional authentication and validation coverage.

## Objectives
- Validate the most critical customer journeys and system behaviors.
- Use automation to detect regressions in UI, API, and E2E flows.
- Verify that performance and accessibility requirements are honored for critical pages.
- Produce measurable results for quality gates and release readiness.

## Test Strategy by Layer

| Layer | Focus | Test Types | Key Risks Addressed |
|---|---|---|---|
| UI (Playwright + .NET) | Navigation, product display, cart UX, responsive layout, feedback messages | Smoke, regression, responsive checks, accessibility verification | Visual breakage, missing feedback, responsive failure |
| API (Playwright + .NET) | Registration/login, product search/filter, cart state, order processing | Functional API tests, contract checks, error-case validation | Data integrity, incorrect filtering, checkout failures |
| E2E (Playwright + .NET) | End-to-end purchase and session flows | Scenario-based journeys, cross-layer validation | Cart persistence, order generation, session continuity |
| Performance (JMeter) | Homepage and API latency, baseline concurrency | Load tests, threshold validation | Slow page/API response, regression in key metrics |

## Test Environments
- Primary: Dedicated QA or staging instance of `automationexercise.com` when available.
- Secondary: Public instance only if no isolated QA environment exists.
- Supported browsers: Chrome-based browser for Playwright automation.
- Devices: viewport sets representing Desktop, Tablet, and Mobile.

## Test Data Strategy
1. Reusable stable user accounts for login and registration validation.
2. Deterministic product selections for automation stability (e.g., known product IDs or visible catalog items).
3. Defined shipping and dummy payment values for checkout scenarios.
4. Session isolation for E2E checkout and cart workflows.

## Test Execution Approach
- Execute smoke and regression suites for each layer.
- Use risk-prioritized scenarios first, then broader regression coverage.
- Track automation results using pass/fail status and evidence links.
- Capture failures with screenshots, logs, and API traces.

### Minimum viable test groups
1. Smoke tests for homepage navigation, search, add-to-cart, checkout, and login.
2. API tests for product retrieval, filtering, registration, login, and order submission.
3. E2E scenarios for end-to-end user journeys.
4. Performance validation of homepage load and key API latency.

## Exit Criteria
- 100% of smoke tests pass.
- Regression pass rate ≥ 95% for core QA coverage.
- No open severity-1 defects in the release scope.
- Homepage median load < 2.0s and 95th percentile API latency < 200ms.
- Accessibility and responsive checks completed for critical pages.

## Deliverables
- Executed test reports for UI, API, and E2E suites.
- Performance summary from JMeter runs.
- Defect log and regression evidence.
- Signed QA release readiness note with coverage metrics.
