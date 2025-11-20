# Service Specification README

Use this folder to capture specifications for a single service inside a monorepo. Copy `service-sample/` for each microservice and rename the directory to match the service (e.g., `service-auth/`).

Recommended sections:
- `contracts/`: Folder containing API definitions (OpenAPI, AsyncAPI, Proto, GraphQL) and consumer contracts.
- `decisions/`: Folder for service-specific Architecture Decision Records (ADRs).
- `ARCHITECTURE.md`: Service-specific component view and dependencies; link back to `../platform/ARCHITECTURE.md`.
- `API_REFERENCE.md`: Endpoints, queues, or jobs owned by this service.
- `DATA_MODELS.md`: Schemas owned by the service or extensions of shared models.
- `TESTING.md`: Local quality strategy and coverage details.
- `OBSERVABILITY.md`: Metrics/logs/traces unique to this service plus inherited alerts.
- `DEPLOYMENT.md`: Rollout steps, feature flag usage, environment-specific notes.
- `SECURITY.md`: Threat model and control mapping specific to the service; note variances from `../../platform/SECURITY.md`.

Keep links to shared specs (platform folder) so readers can navigate between global and local context.
