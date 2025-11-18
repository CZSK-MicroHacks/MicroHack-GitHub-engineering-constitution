# Shared Security Standard

Use this document to capture security controls that every service in the monorepo must honor. Service-level `SECURITY.md` files should reference this baseline and document only the additional, local requirements or exceptions.

## Threat Modeling Expectations
- Required methodology (e.g., STRIDE, PASTA) and when to run it (per major feature, quarterly review, before GA).
- Assets and trust boundaries that must appear in each service threat model.

## Identity & Access
- Authentication mechanism (Azure AD, OAuth2) and token standards.
- Authorization pattern (RBAC, ABAC) and required enforcement layers.
- Secrets management strategy (Key Vault, managed identities), rotation cadence, and auditing requirements.

## Data Protection
- Classification levels and handling expectations (Public, Internal, Confidential, Restricted).
- Encryption requirements in transit and at rest.
- Key management and approved cryptographic libraries.

## Secure Coding & Dependencies
- Approved SAST/DAST tools and scan frequency.
- Dependency scanning rules (pip-audit, npm audit, etc.) with severity thresholds for blocking releases.
- Logging/monitoring obligations for security events.

## Incident Response & Compliance
- On-call rotation expectations, escalation channels, and response SLAs.
- Evidence storage requirements for audits (duration, systems).

## Specification by Example
Add shared scenarios (e.g., "Given an API call lacks a valid tenant token, the gateway returns 401 and logs event SEC-01") and link to automated security tests.

## Exceptions
Describe how teams request temporary exceptions, required data (risk, mitigation, expiry), and who approves them.
