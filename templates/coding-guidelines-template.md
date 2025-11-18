# Coding Guidelines Template

> Copy this file into your service repository (do not edit in place) and tailor the guidance to the technology stack in scope.

## 1. Overview
- **Service / Component**:
- **Owning Team**:
- **Last Updated**:
- **Reference Specs**: Link to `docs/REQUIREMENTS.md`, `docs/DESIGN.md`, related ADRs/PRDs.

## 2. Principles
_List the top 3–5 non-negotiable engineering principles (e.g., spec-first implementation, observability, performance budgets)._ 

## 3. Architecture Summary
- Languages / frameworks used
- Key modules or layers
- External dependencies (DBs, queues, third-party APIs)

## 4. Coding Conventions
| Area | Standard | Notes / Examples |
| --- | --- | --- |
| Naming | e.g., `snake_case` for functions | |
| Formatting | e.g., `ruff`, `prettier` | |
| Error Handling | e.g., wrap external calls, domain exceptions | |
| Logging | e.g., structured JSON logs with request IDs | |

## 5. Specification by Example Scenarios
| Scenario | Example | Automated Test? |
| --- | --- | --- |
| `<User story>` | `<Given/When/Then>` | `Yes/No` |

## 6. Dependencies & Tooling
- Package manager & minimum versions
- Required lint, type-check, and test commands
- Security scanners

## 7. Testing Strategy
- Unit testing approach
- Integration/contract testing expectations
- Coverage thresholds

## 8. Performance & Observability
- Target SLIs/SLOs
- Logging/metrics/tracing requirements
- Dashboards or alert rules

## 9. Security
- Secrets handling strategy
- Authentication/authorization baseline
- Data classification + handling rules

## 10. Review Checklist
Create a short checklist reviewers can run through before approving changes (naming, tests updated, specs updated, etc.).

## 11. Change History
| Date | Author | Summary |
| --- | --- | --- |
