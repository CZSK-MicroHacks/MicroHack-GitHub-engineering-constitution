# Service Deployment Plan

Describe how this service moves from commit to production, referencing shared workflows in `../../platform/DEPLOYMENT.md`.

## Pipelines
- CI stages (linting, tests, scans)
- CD stages (artifact build, deploy job, verifications)

## Environments
| Environment | Branch/Artifact | Purpose | Approvals |
| --- | --- | --- | --- |

## Release Steps
1. Preconditions
2. Deployment procedure (feature flags, canary %)
3. Verification & rollback

## Infrastructure
List service-specific infrastructure (e.g., dedicated Cosmos containers, Service Bus queues) and link to IaC definitions.
