# Shared Deployment Strategy

Capture the release workflow and infrastructure expectations that apply across all services in the monorepo.

## Environments
| Environment | Purpose | Source Branch / Tag | Promotion Criteria |
| --- | --- | --- | --- |

## CI/CD Pipeline
- Required stages (lint, tests, scans, artifact build, deploy, verification).
- Tooling (GitHub Actions, Azure DevOps) and reusable workflows/templates.
- Artifact storage and retention requirements.

## Release Patterns
- Supported strategies (rolling, blue/green, canary, feature flags) and when to use each.
- Rollback expectations and time-to-recover targets.

## Approvals & Compliance
- Mandatory approvals (e.g., code owners, security) for production deploys.
- Evidence bundle requirements (test reports, scan outputs) and storage locations.

## Specification by Example
Add scenarios that describe the expected behavior (e.g., "Given a failed canary, the pipeline automatically halts and rolls back within 5 minutes").

Services should reference this file in their local `DEPLOYMENT.md` and capture only the additional, service-specific steps (custom feature flags, data migrations, dependency sequencing).
