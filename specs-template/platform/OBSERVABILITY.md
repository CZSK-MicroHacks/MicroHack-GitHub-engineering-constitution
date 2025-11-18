# Shared Observability Strategy

Use this document to capture telemetry standards that apply to every service in the monorepo.

## Instrumentation Baseline
- Preferred library/SDK (e.g., OpenTelemetry) and version requirements.
- Propagation format (W3C tracecontext) and expectations for correlation IDs.
- Logging format (JSON, ECS fields) and mandatory attributes (requestId, tenantId, userId hash).

## Metrics & SLOs
List organization-wide SLIs/SLOs plus guidance on which services must emit them.

| Metric | Definition | Target/SLO | Collection Notes |
| --- | --- | --- | --- |

## Tracing
- Sampling strategy (head-based, tail-based) and default sampling rates.
- Span naming conventions and attributes every service must set.

## Logging
- Logging levels allowed in production.
- PII/PCI masking rules.
- Retention expectations and downstream sinks (SIEM, Data Lake, etc.).

## Alerting & Dashboards
- Shared dashboards and on-call channels.
- Naming convention for alerts (e.g., `<service>-<metric>-alert`).

## Specification by Example
Capture a few multi-service observability scenarios (e.g., "Given request traverses API → Payments → Notifications, we can trace it end-to-end within 5 seconds").

Each service's `OBSERVABILITY.md` should reference this file and only describe service-specific metrics or overrides.
