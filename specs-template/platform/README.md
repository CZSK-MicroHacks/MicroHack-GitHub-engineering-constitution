# Platform-Level Specifications

Use this folder for documentation that spans multiple services within a monorepo. Keep it lightweight—only add documents when a contract or decision truly applies to more than one service.

## Recommended Contents
- `ARCHITECTURE.md`: System context, shared diagrams, integration boundaries, and cross-cutting concerns.
- `DATA_MODELS.md`: Canonical schemas for events, shared tables, or reusable Pydantic models.
- `OBSERVABILITY.md`: Organization-wide instrumentation and telemetry guidance (e.g., OpenTelemetry usage, shared SLOs).
- `TESTING.md`: Baseline testing expectations (pyramid targets, CI gates) every service must meet.
- `DEPLOYMENT.md`: Release workflow, environment definitions, and compliance requirements applied to all services.
- `SECURITY.md`: Shared security posture, control requirements, scanning expectations, and incident response guidance.

## Optional Files
If additional cross-service requirements emerge (e.g., shared security controls, incident response runbooks), copy the relevant service template file into this folder and rename it clearly (for example, `SECURITY.shared.md`). Reference these shared docs from each service spec instead of duplicating content.

## When to add a platform document
1. Multiple services depend on the same contract or operational process.
2. Changes require coordination across teams.
3. You need a single source of truth for audits or onboarding.

If a concern is isolated to a single service, keep it inside `services/<service-name>/` and link back here only when necessary.
