**Assumptions & Questions Backlog**

**Assumptions (explicit, traceable to missing info)**
1. The `/api_list` page provides the authoritative API contract for automation; endpoints listed there are stable for test design.
2. Dummy payment flow is sufficient for validating checkout and Order ID generation; no real payment provider integration is required.
3. Responsive validation will be performed via device-width breakpoints (320px–1920px) rather than an exhaustive browser/device matrix.
4. Performance targets listed in `Requirements v1.md` (homepage load, concurrent users, API latency) are the acceptance thresholds for QA performance testing.
5. Accessibility scope is WCAG 2.1 AA checks described in `Requirements v1.md` (keyboard navigation, alt text, labels, color contrast, semantic HTML).

**Open Questions (actionable — to Product / Dev / Security)**
- Environments & Access
  1. Is there a dedicated QA/staging instance separate from the public site that QA can run destructive tests against? If yes, provide URL and credentials.
  2. Are there environment reset or cleanup scripts (DB/seeds) available to return test data to baseline after automation runs?

- Test Data & Accounts
  3. Should QA use shared stable test accounts or create disposable accounts per test run? Any account naming or seeding rules?
  4. Is there an approved, non-sensitive shipping and dummy payment dataset we should use for checkout tests?

- API & Docs
  5. Are all endpoints shown in `/api_list` intended to be automated, or should automation focus only on endpoints tied to the user/product/order flows in `Requirements v1.md`?
  6. Do any API endpoints require keys or authentication beyond standard registration/login flows? If yes, provide details.

- Non-Functional & Release
  7. Beyond the performance metrics in `Requirements v1.md`, are there additional operational SLAs (monitoring/alert thresholds) QA should validate or report against?
  8. For release sign-off, besides QA Manager approval, are there other stakeholders (product, operations) whose explicit sign-off is required?

- Accessibility
  9. Should accessibility testing include manual screen reader validation (NVDA/VoiceOver) for critical flows, or are automated WCAG checks sufficient?

**Gap Register (explicit missing items that block automation scope)**
- Existence and URL of a dedicated QA/staging instance to run destructive/isolated tests.
- Stable test accounts and a canonical test data set for checkout.
- Clarification on API authentication details (if any) beyond registration/login.

(End of assumptions & questions backlog.)
