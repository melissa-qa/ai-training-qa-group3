# Control Plane: Traceability Matrix

**Purpose:** Map acceptance criteria to test cases, associated risks, quality gates, and evidence collection points for `automationexercise.com` QA.

**Source Documents:**
- [UserStories.md](docs/03-test-pack-control-plane/UserStories.md)
- [test-pack.md](docs/03-test-pack-control-plane/manual-tests/test-pack.md)
- [Risk Matrix](docs/01-strategy/risk-matrix.md)
- [Quality Gates](docs/01-strategy/quality-gates.md)

---

## Traceability Matrix

| Story / AC | Test Case ID | Risk # | Risk Description | Gate | EvidenceLink |
|---|---|---|---|---|---|
| AE-1 AC 1 | TC-AE1-005 | #8 | Navigation Links — Header or main links broken / incorrect destinations | PR (Smoke) | [Placeholder: header_navigation_evidence] |
| AE-1 AC 2-3 | TC-AE1-003 | #2 | User Management — Duplicate email registration allowed or valid users blocked | PR | [Placeholder: form_validation_evidence] |
| AE-1 AC 2 | TC-AE1-002 | #2 | User Management — Duplicate email registration allowed or valid users blocked | PR / Nightly | [Placeholder: duplicate_email_evidence] |
| AE-1 AC 2 | TC-AE1-006 | #2 | User Management — Duplicate email registration allowed or valid users blocked | PR | [Placeholder: email_validation_evidence] |
| AE-1 AC 2-4 | TC-AE1-001 | #2 | User Management — Duplicate email registration allowed or valid users blocked | PR / Nightly | [Placeholder: successful_registration_evidence] |
| AE-1 AC 4 | TC-AE1-004 | #2 | User Management — Duplicate email registration allowed or valid users blocked | PR / Nightly | [Placeholder: account_created_message_evidence] |
| AE-1 AC 4 | TC-AE1-007 | #2 | User Management — Duplicate email registration allowed or valid users blocked | Nightly | [Placeholder: post_registration_login_evidence] |
| AE-2 AC 1-3 | TC-AE2-001 | #2 | User Management — Duplicate email registration allowed or valid users blocked | PR / Nightly | [Placeholder: valid_login_evidence] |
| AE-2 AC 1-3 | TC-AE2-002 | #2 | User Management — Duplicate email registration allowed or valid users blocked | PR | [Placeholder: invalid_password_evidence] |
| AE-2 AC 1-3 | TC-AE2-003 | #2 | User Management — Duplicate email registration allowed or valid users blocked | Nightly | [Placeholder: locked_account_evidence] |
| AE-2 AC 1-3 | TC-AE2-004 | #9 | Session Persistence — User/cart session lost across navigation or sessions | Nightly | [Placeholder: session_persistence_evidence] |
| AE-2 AC 1-3 | TC-AE2-005 | #2 | User Management — Duplicate email registration allowed or valid users blocked | PR | [Placeholder: injection_resistance_evidence] |
| AE-2 AC 1-3 | TC-AE2-006 | #7 | Accessibility — Keyboard navigation or alt text missing on critical pages | PR | [Placeholder: accessibility_login_evidence] |
| AE-3 AC 1-2 | TC-AE3-001 | #2 | User Management — Duplicate email registration allowed or valid users blocked | PR / Nightly | [Placeholder: logout_evidence] |
| AE-3 AC 1-2 | TC-AE3-002 | #9 | Session Persistence — User/cart session lost across navigation or sessions | Nightly / Release | [Placeholder: access_control_evidence] |
| AE-3 AC 1 | TC-AE3-003 | #8 | Navigation Links — Header or main links broken / incorrect destinations | PR (Smoke) | [Placeholder: header_logout_link_evidence] |
| AE-3 AC 1-2 | TC-AE3-004 | #2 | User Management — Duplicate email registration allowed or valid users blocked | Nightly | [Placeholder: session_cleanup_evidence] |
| AE-3 AC 1-2 | TC-AE3-005 | #7 | Accessibility — Keyboard navigation or alt text missing on critical pages | PR | [Placeholder: accessibility_logout_evidence] |
| AE-4 AC 1-3 | TC-AE4-001 | #3 | Search & Filter — Search/filter returns incorrect or incomplete product lists | PR / Nightly | [Placeholder: exact_match_search_evidence] |
| AE-4 AC 1-3 | TC-AE4-002 | #3 | Search & Filter — Search/filter returns incorrect or incomplete product lists | Nightly | [Placeholder: partial_search_evidence] |
| AE-4 AC 1-3 | TC-AE4-003 | #3 | Search & Filter — Search/filter returns incorrect or incomplete product lists | PR | [Placeholder: no_results_evidence] |
| AE-4 AC 1-3 | TC-AE4-004 | #5 | Performance — Homepage load >2s or API latency >200ms | Release | [Placeholder: search_performance_evidence] |
| AE-4 AC 1-3 | TC-AE4-005 | #2 | User Management — Duplicate email registration allowed or valid users blocked | PR | [Placeholder: search_injection_evidence] |
| AE-4 AC 1-3 | TC-AE4-006 | #6 | Responsive Layout — Layout breaks on mobile/tablet widths | Nightly | [Placeholder: search_responsive_evidence] |
| AE-5 AC 1-3 | TC-AE5-001 | #4 | Cart Calculations — Incorrect item quantities or totals in cart | PR / Nightly | [Placeholder: add_single_product_evidence] |
| AE-5 AC 1-3 | TC-AE5-002 | #4 | Cart Calculations — Incorrect item quantities or totals in cart | Nightly | [Placeholder: add_multiple_products_evidence] |
| AE-5 AC 1-3 | TC-AE5-003 | #4 | Cart Calculations — Incorrect item quantities or totals in cart | Nightly | [Placeholder: quantity_increment_evidence] |
| AE-5 AC 1-3 | TC-AE5-004 | #3 | Search & Filter — Search/filter returns incorrect or incomplete product lists | PR | [Placeholder: recommended_items_evidence] |
| AE-5 AC 1-3 | TC-AE5-005 | #9 | Session Persistence — User/cart session lost across navigation or sessions | Nightly / Release | [Placeholder: cart_persistence_evidence] |
| AE-5 AC 1-3 | TC-AE5-006 | #7 | Accessibility — Keyboard navigation or alt text missing on critical pages | PR | [Placeholder: cart_accessibility_evidence] |

---

## Coverage Summary

| Gate | Count | Stories | Risk Coverage |
|---|---|---|---|
| PR | 14 | AE-1, AE-2, AE-3, AE-4, AE-5 | #2, #6, #7, #8 |
| PR (Smoke) | 2 | AE-1, AE-3 | #8 |
| PR / Nightly | 8 | AE-1, AE-2, AE-4, AE-5 | #2, #3, #4 |
| Nightly | 13 | AE-1, AE-2, AE-3, AE-4, AE-5 | #2, #3, #4, #5, #6, #9 |
| Nightly / Release | 3 | AE-3, AE-5 | #9 |
| Release | 1 | AE-4 | #5 |

---

## Filling Evidence Links

When tests are executed, replace the placeholder values with actual evidence:
- Screenshots: `[Screenshot: add_to_cart_flow_20260605.png]`
- Test reports: `[Report: PR-gate-AE5-001-20260605.html]`
- Video recordings: `[Video: registration_flow_20260605.mp4]`
- Defect links: `[Defect: BUG-123 - Cart totals incorrect]`
- Measurement tools: `[Perf: JMeter report homepage_baseline_20260605.jtl]`

---

## Risk-to-Gate Mapping

| Risk # | Risk Description | Tests Assigned | Primary Gate | Secondary Gate |
|---|---|---|---|---|
| #2 | User Management — Duplicate email, invalid users, validation | 15 tests | PR / Nightly | Nightly |
| #3 | Search & Filter — Incorrect filtering/results | 5 tests | PR / Nightly | Nightly |
| #4 | Cart Calculations — Incorrect quantities/totals | 3 tests | Nightly | PR / Nightly |
| #5 | Performance — Load/latency breaches | 1 test | Release | Nightly |
| #6 | Responsive Layout — Layout breaks | 1 test | Nightly | PR |
| #7 | Accessibility — Keyboard/labels missing | 4 tests | PR | Nightly |
| #8 | Navigation Links — Broken links | 2 tests | PR (Smoke) | PR |
| #9 | Session Persistence — Cart/session loss | 4 tests | Nightly / Release | Nightly |

---

## Test Execution Workflow

1. **PR Gate:** Execute all tests tagged with `PR` or `PR (Smoke)`.
2. **Nightly Gate:** Execute all tests tagged with `Nightly`.
3. **Release Gate:** Execute all tests tagged with `Release`.
4. **Capture Evidence:** Link test output (screenshots, reports, videos) to corresponding EvidenceLink placeholders.
5. **Report Status:** Tally pass/fail counts per story and risk; confirm gate approval criteria.

---

## Notes

- Each test case is traceable to at least one acceptance criterion and one risk.
- Multiple test cases may cover the same risk to ensure layered validation (positive, negative, edge cases).
- Evidence links should be filled after test execution to maintain a complete audit trail.
- For regression cycles, reuse this matrix to confirm coverage consistency.
