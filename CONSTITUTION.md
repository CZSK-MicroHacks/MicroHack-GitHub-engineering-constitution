# MicroHack Engineering Constitution

## 1. Mission
Provide a durable governance backbone for every MicroHack software initiative so that teams deliver consistent, auditable, and secure solutions using spec-driven development and Specification by Example practices.

## 2. Scope
This constitution applies to:
- All codebases, services, data pipelines, and AI agents created by MicroHack teams.
- Shared tooling (CI/CD, deployment, observability) that impacts multiple services.
- Documentation hosted in `docs/` across repos (requirements, design, testing, deployment, data models).

## 3. Core Principles
1. **Spec First** – Begin with written requirements, examples, and acceptance criteria before writing production code.
2. **Single Source of Truth** – Keep specifications, standards, and templates versioned alongside code; no private forks of policy documents.
3. **Small, Composable Units** – Prefer cohesive modules and incremental change over big-bang deliveries.
4. **Explicit Contracts** – Document data models, APIs, and integrations with unambiguous schemas (Pydantic models, OpenAPI, JSON Schema, etc.).
5. **Observable Systems** – Instrument services with logging, metrics, and tracing sized to the service criticality tier.
6. **Secure by Default** – Treat secrets, access control, and dependency hygiene as table stakes; security exemptions require documented approval.
7. **Learning Feedback Loop** – Translate incidents, audits, and retrospectives into updates to this constitution, standards, or templates.

## 4. Spec-Driven Development Commitments
- **Specification by Example**: express requirements as concrete, user-focused scenarios that can be automated as tests. Keep them in sync with behavior changes.
- **Docs as Gatekeepers**: meaningful code changes require corresponding updates to `docs/` (REQUIREMENTS, DESIGN, DATA_MODELS, API_REFERENCE, TESTING, DEPLOYMENT).
- **Implementation Log Discipline**: each repo maintains `docs/IMPLEMENTATION_LOG.md` as the durable record of architectural decisions and rationale.
- **Template Reuse**: ADR, PRD, and security templates provided here must be copied (not moved) into service repositories and filled before major changes.

## 5. Governance and Change Control
- **Tiered Approval**: decisions follow the RACI matrix in `GOVERNANCE.md`; breaking changes or cross-team standards require Architecture Council approval.
- **RFC Workflow**: proposals for constitutional amendments, new standards, or template changes flow through the RFC process before merging.
- **Sunset Policy**: retired standards stay archived for six months, then move to `/archive` with rationale and replacement guidance.

## 6. Compliance & Audits
- **Traceability**: every production deployment must point to an approved spec (PRD/ADR) and the implementation log entry capturing verification.
- **Evidence Bundle**: CI pipelines must persist lint/test/scan artifacts for 90 days. Failing to store evidence blocks release promotions.
- **Security Reviews**: critical releases undergo threat modeling using the security template; results attach to the RFC.

## 7. Change Process
1. Draft RFC using the governance workflow.
2. Engage impacted stakeholders; capture feedback in the RFC record.
3. Secure approvals (Architecture Council, Security, Product) per `GOVERNANCE.md`.
4. Merge updates and announce in #engineering-gov Slack channel with effective date.
5. Update onboarding material or runbooks when the change affects day-to-day execution.

## 8. Enforcement
- Persistent non-compliance triggers remediation plans and, if needed, release freeze until obligations are met.
- Automated policy-as-code checks (lint rules, CI guards) should enforce standards wherever possible.
- Exceptions are time-boxed, documented, and revisited during quarterly governance reviews.

## 9. Living Document
This constitution evolves through transparent RFCs, reflecting new lessons from delivery, audits, and experiments. Everyone is responsible for proposing improvements when they find gaps or redundancies.
