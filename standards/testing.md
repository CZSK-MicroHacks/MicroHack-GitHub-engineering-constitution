# Testing Standard

## 1. Testing Philosophy
- Tests embody Specification by Example scenarios: concrete behaviors that define success.
- Aim for fast feedback: 10-minute max for required CI test suites.
- Prefer smaller, composable tests over slow, brittle system tests.

## 2. Test Pyramid Targets
| Layer | Purpose | Target Coverage |
| --- | --- | --- |
| Unit | Validate functions/classes in isolation using mocks. | 70%+ lines |
| Integration | Exercise modules plus IO boundaries (DB, external APIs). | Critical flows |
| Contract | Verify API/queue contracts between services (PACT / schema validation). | All published endpoints |
| End-to-End / UI | Validate user journeys referenced in PRDs. | Smoke + high-risk flows |

## 3. Workflow Expectations
1. Write/refresh tests when updating specs (requirements, design, data models).
2. Use red-green-refactor: add failing test per scenario, implement fix, refactor safely.
3. Keep test data close to specs; prefer builders/factories describing intent.
4. Update documentation (`specs/**/TESTING.md`) with new strategies or coverage adjustments.

## 4. Tooling
Specific tooling choices are defined in the respective language engineering standards (e.g., `standards/python.md`, `standards/typescript.md`).

- **Contract Tests**: PACT, OpenAPI schema validation in CI; failing contracts block deployments.
- **Load/Performance**: k6, Locust, or Azure Load Testing for critical services; document thresholds in PRD/ADR.

## 5. Quality Gates
- CI must run: linting, static analysis, unit tests, integration tests (where feasible), dependency scans, and coverage reports.
- Enforce minimum coverage thresholds per repo. Failing to meet thresholds requires waiver from Architecture Council.
- Snapshot or visual regression updates require design/PM review.

## 6. Test Data Management
- Use synthetic/anonymized data sets stored in secure artifacts.
- For integration/E2E tests, provision ephemeral environments or use Dockerized dependencies (Cosmos DB emulator, PostgreSQL, etc.).
- Tear down resources after tests to control cost and prevent drift.

## 7. Observability of Tests
- Capture and store test artifacts (logs, screenshots, coverage reports) for 30+ days.
- Link failing test runs to the corresponding RFC or implementation log entry when triaging recurring issues.

## 8. Flakiness Policy
- Flaky tests block the build until fixed or quarantined with an issue reference and remediation date.
- Track flaky tests in a shared backlog; review status during the monthly governance sync.

## 9. Release Readiness Checklist
- All Specification by Example scenarios automated.
- Regression suite green twice consecutively on main branch.
- Performance tests meet PRD-defined SLAs.
- Security/regression scans clean or approved with documented exceptions.
