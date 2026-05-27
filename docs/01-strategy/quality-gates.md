**Quality Gates: Pull Request / Nightly / Release**

All gates are measurable and tied to test evidence.

**Pull Request Gate**
- Scope: changed feature area and immediate dependencies.
- Measurable criteria:
  1. All affected smoke tests pass (100% pass rate for smoke tests run against PR scope).
  2. Minimum 80% test coverage for the modified feature area (unit/API/UI where applicable).
  3. No open critical (severity-1) defects in the PR scope.
  4. No new automated accessibility violations on modified pages.
- Evidence required: PR automation report (test run), coverage report, defect list.

**Nightly Gate**
- Scope: full regression suite and stability checks.
- Measurable criteria:
  1. Full regression suite executed; core regression pass rate ≥ 95%.
  2. Flakiness: ≤ 3 flaky tests reported (identified and triaged within 24h).
  3. Performance drift ≤ 10% from baseline for key metrics (homepage median load, API median latency).
  4. No new high-severity accessibility regressions.
- Evidence required: Nightly test report, flakiness report, performance baseline comparison.

**Release Gate**
- Scope: release readiness for deployment to production/similar environment.
- Measurable criteria:
  1. 100% smoke and release regression pass for critical journeys.
  2. No open severity-1 or severity-2 defects.
  3. Performance acceptance: homepage median load < 2.0s; 95% of API requests < 200ms.
  4. Accessibility acceptance: critical paths keyboard-navigable and no outstanding WCAG AA-level critical issues.
  5. Test evidence and defect closure report available and approved by QA Manager.
- Evidence required: Release test summary, performance report, accessibility verification, defect closure list.

**Gate Summary Table**
| Gate | Scope | Measurable Criteria | Evidence |
|---|---|---|---|
| PR | Feature change | Smoke pass (100%), ≥80% feature coverage, no Sev1 defects | PR report, coverage, defects |
| Nightly | Full regression | Regression ≥95% pass, ≤3 flaky tests, ≤10% performance drift | Nightly report, perf comparison |
| Release | Release readiness | 100% smoke/regression, no Sev1/2, perf thresholds met | Release dossier (reports + approvals) |

**Notes**
- Coverage metrics should be scoped to the feature or module under change — not global coverage alone.
- Flaky tests must be triaged and either fixed, quarantined with justification, or documented with mitigation steps.
