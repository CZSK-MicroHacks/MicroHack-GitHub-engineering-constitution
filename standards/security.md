# Security Standard

## 1. Objectives
Ensure every MicroHack system is secure by default, auditable, and resilient to known threats while enabling rapid delivery.

## 2. Baseline Controls
- **Identity & Access**: Use least-privilege identities managed through Azure AD or equivalent. Rotate credentials automatically; forbid shared accounts.
- **Secrets Management**: Store secrets in Azure Key Vault or platform secrets manager. Access via managed identities; never commit secrets or store them in CI logs.
- **Encryption**: Enforce TLS 1.2+ in transit and provider-managed encryption at rest. Document any exception via RFC.
- **Dependency Hygiene**: Run SCA scans (`pip-audit`, `npm audit`, `pnpm audit`, `Safety`) on every merge. Address critical/high findings before release.

## 3. Secure Development Lifecycle
1. **Spec Phase**: Include threat models within PRDs/ADRs. Reference Specification by Example scenarios covering abuse cases.
2. **Implementation**: Follow language standards (Python/TypeScript). Apply secure defaults (parameterized queries, prepared statements, safe serialization).
3. **Verification**: Integrate SAST, DAST, and container scans in CI/CD. Record evidence in the implementation log.
4. **Release**: Ensure operational readiness review covers logging, monitoring, and incident response playbooks.

## 4. Logging & Monitoring
- Emit structured logs with request IDs, user IDs (hashed), and correlation IDs for distributed tracing.
- Forward logs to centralized SIEM with retention aligned to compliance requirements.
- Define security metrics: auth failures, privilege escalations, rate-limit breaches, anomaly scores.

## 5. Access Control & Data Governance
- Classify data (Public, Internal, Confidential, Restricted) and document handling rules in `docs/DATA_MODELS.md`.
- Implement role-based access at the API layer; avoid client-enforced authorization.
- For multi-tenant data, use partition keys (e.g., tenantId) to isolate access and minimize cross-partition queries when using Azure Cosmos DB.

## 6. Testing & Validation
- Maintain security regression tests verifying authz/authn, rate limiting, input validation, and sensitive data redaction.
- Run regular pen tests or bug bounty engagements for high-risk services.
- Add Specification by Example scenarios for critical security flows (e.g., password reset, MFA enrollment, API key rotation).

## 7. Incident Response
- Keep on-call rotations documented, with escalation paths and runbooks.
- Record incidents in the governance backlog, including root cause, blast radius, remediation, and lessons learned.
- Update standards/templates when incidents reveal policy gaps.

## 8. Compliance & Audits
- Maintain evidence bundles for at least 90 days (lint/test/scan outputs, deployment manifests).
- Review compliance status quarterly; log findings and actions in `docs/IMPLEMENTATION_LOG.md` or the governance tracker.

## 9. Exceptions
- File security exceptions via RFC with risk/impact analysis and mitigation plan.
- Default expiration: 90 days. Extend only with Security Lead approval.
