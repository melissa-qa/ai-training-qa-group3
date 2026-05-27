**Ranked Risk Matrix: automationexercise.com**

Ranked top risks (high impact first, then high probability). Each risk shows impact rationale, what coverage looks like, and which quality gate is affected.

| Rank | Module | Risk | Impact Rationale | Probability | Coverage (what 'good' looks like) | Quality Gate Affected |
|---:|---|---|---|---:|---|---|
| 1 | Checkout / Order Processing | Order processing fails or no Order ID generated | High: prevents completion of purchase flow and order confirmation | High | E2E checkout scenarios, API validation, smoke test for order creation | Release |
| 2 | User Management | Duplicate email registration allowed or valid users blocked | High: blocks onboarding and causes user data issues | High | API validation tests, duplicate-account negative tests, E2E signup | PR / Nightly |
| 3 | Search & Filter | Search/filter returns incorrect or incomplete product lists | High: degrades discovery and conversion | High | API filter contract tests, UI search regression, E2E browsing | Nightly |
| 4 | Cart Calculations | Incorrect item quantities or totals in cart | High: billing errors and UX trust loss | Medium | UI cart checks, API cart-state tests, regression checks | Nightly |
| 5 | Performance (Homepage/API) | Homepage load >2s or API latency >200ms | High: breaches performance requirements and SLAs | Medium | JMeter load tests, baseline comparisons, performance smoke | Release |
| 6 | Responsive Layout | Layout breaks on mobile/tablet widths | Medium: poor usability on supported devices | High | Visual/responsive tests across width set, manual checks | PR / Nightly |
| 7 | Accessibility | Keyboard navigation or alt text missing on critical pages | Medium: accessibility compliance failure (WCAG 2.1 AA) | Medium | Automated accessibility scans, targeted manual keyboard checks | PR / Release |
| 8 | Navigation Links | Header or main links broken / incorrect destinations | Medium: users cannot reach key pages | Medium | UI smoke for header links, link integrity checks | PR |
| 9 | Session Persistence | User/cart session lost across navigation or sessions | Medium: broken shopping continuity | Medium | API state tests, E2E sessions, session-resume tests | Nightly |
| 10 | API Documentation | `/api_list` inaccurate or incomplete for automation planning | Low: planning risk and fragile automation | Medium | Documentation validation, API discovery checks | PR |

Notes:
- Impact Rationale: concise justification drawn from `Requirements v1.md` (customer-facing flows, performance constraints, accessibility needs).
- Coverage: describes measurable tests and success criteria that mitigate the risk (e.g., "E2E checkout scenarios" means X scenarios executed and passing).
- Quality Gate: indicates the gate where the risk mitigation is enforced (PR, Nightly, Release).

(Each ranked risk should be traceable to tests and measurable acceptance criteria in automation suites.)
