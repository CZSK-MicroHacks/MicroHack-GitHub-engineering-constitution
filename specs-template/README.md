# Specification Workspace

The `specs-template/` folder provides the canonical specification workspace for any MicroHack project. Copy or scaffold this entire directory into your service repository (usually under `docs/specs/`) and keep each file version-controlled alongside code. After copying you can rename the folder to `specs/` in the target repo for clarity.

## Folder layout
```
specs-template/
	README.md
	platform/
		README.md
		ARCHITECTURE.md
		DATA_MODELS.md
		OBSERVABILITY.md
		TESTING.md
		DEPLOYMENT.md
		SECURITY.md
	services/
		service-sample/
			README.md
			ARCHITECTURE.md
			DATA_MODELS.md
			API_REFERENCE.md
			OBSERVABILITY.md
			TESTING.md
			DEPLOYMENT.md
			SECURITY.md
```

## How to use this structure
1. **Copy the folder**: duplicate `specs-template/` into your target repository (e.g., `docs/specs/`).
2. **Rename directories**: keep `platform/` for cross-service specs and copy `services/service-sample/` for each real service (rename to `service-<name>/`).
3. **Keep files focused**: each markdown file owns a single domain (data models, API, testing, etc.) so updates stay concise and reviewable.
4. **Link liberally**: reference ADRs, PRDs, and implementation log entries for traceability.
5. **Specification by Example**: capture concrete Given/When/Then scenarios in every file where behavior matters (APIs, testing, observability alerts, deployment runbooks).

## File overview
| File | Purpose |
| --- | --- |
| `platform/README.md` | Explains how to add shared specs only when multiple services depend on them. |
| `platform/ARCHITECTURE.md` | High-level diagrams, component responsibilities, integration points, and decision references shared by all services. |
| `platform/DATA_MODELS.md` | Structured schemas for canonical data contracts (Pydantic models, database tables, event payloads). |
| `platform/OBSERVABILITY.md` | Organization-wide instrumentation guidance, metrics, logs, traces, and alert standards. |
| `platform/TESTING.md` | Shared testing philosophy, pyramid targets, tooling baselines, and CI quality gates. |
| `platform/DEPLOYMENT.md` | Cross-service release workflows, environment definitions, and compliance expectations. |
| `platform/SECURITY.md` | Shared security posture, control requirements, scanning expectations, and incident response guidance. |
| `services/service-sample/*` | Service-level versions of each document (API reference, data models, observability, testing, deployment, security). Copy/rename per service. |

> Need additional shared docs (incident response, privacy, etc.)? Copy the relevant service template file into `platform/` (or create `RUNBOOK.shared.md`, etc.) and point each service spec at it instead of duplicating content.

## Workflow expectations
- Update specifications as part of every PR that changes behavior.
- Reference Specification by Example scenarios in `API_REFERENCE.md` and `TESTING.md` to keep docs executable.
- When specs change materially, log the decision in `docs/IMPLEMENTATION_LOG.md` (or equivalent) and link back here.

## Monorepo / Multi-Service Guidance
For repositories that host multiple services, keep one shared spec plus service-specific copies of this template:

```
docs/
	specs/
		platform/
			README.md
			ARCHITECTURE.md
				DATA_MODELS.md    # Shared schemas/events
				OBSERVABILITY.md
				TESTING.md
				DEPLOYMENT.md
				SECURITY.md
				(optional shared docs)
		services/
			service-auth/
				API_REFERENCE.md
				DATA_MODELS.md   # Service-owned schemas
				TESTING.md
				...
			service-payments/
				...
```

1. **Platform folder (`platform/`)**: copy the template once and document cross-service concerns (global architecture, shared events/schemas, observability, testing, deployment, security). Add optional shared docs only when additional topics emerge.
2. **Service folders (`services/<name>/`)**: copy the template per service for APIs, local data models, testing strategy, and deployment differences. Link back to platform docs (and optional shared files) for inherited rules to avoid duplication.
3. **Schema ownership**: define canonical/shared schemas once under the platform folder. Service folders reference those schemas and only describe extensions or service-owned data.
4. **Exceptions**: when a service diverges from the shared spec, note the variance inside its folder and reference the approving ADR/RFC.

This hierarchy keeps documentation scalable: readers consult the platform spec for global rules, then drill into service folders for implementation details.
