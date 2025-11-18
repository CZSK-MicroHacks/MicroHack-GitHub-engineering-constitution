# Shared Testing Strategy

Define the organization-wide testing expectations that every service must follow before shipping.

## Test Pyramid Targets
| Layer | Goal | Tooling Baseline |
| --- | --- | --- |
| Unit | Fast feedback, run on every PR | pytest, Jest/Vitest, etc. |
| Integration | Validate IO boundaries (DB, queues, external APIs) | Dockerized dependencies, testcontainers |
| Contract | Prevent breaking shared APIs/events | PACT, OpenAPI validation |
| E2E/UX | Verify critical journeys end-to-end | Playwright, Cypress |
| Non-Functional | Load, chaos, security scans | k6, Locust, OWASP ZAP |

## Quality Gates
- Minimum coverage thresholds (e.g., 80% lines/statements) and waiver process.
- Required CI jobs (lint, type-check, unit, integration, contract, e2e smoke) and when they run (PR vs. nightly).
- Dependency/secret scanning requirements.

## Tooling Matrix
Link to shared config for linting, type checking, and testing frameworks so teams can reuse them.

## Specification by Example
Document org-level acceptance criteria (e.g., "Given a shared API contract changes, the consumer contract tests must fail before merge").

Service-level `TESTING.md` files should extend this baseline with details unique to the service (custom fixtures, data sets, additional suites).
