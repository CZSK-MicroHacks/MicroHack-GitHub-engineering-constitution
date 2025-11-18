# Security Standard Template

> Duplicate this template when defining or updating a security standard for a service, platform capability, or organization-wide requirement.

## 1. Document Metadata
- **Standard Name**:
- **Version**:
- **Owner**:
- **Effective Date**:
- **Review Cycle** (e.g., quarterly):
- **Approvals Required**: (Security Lead, Architecture Council, etc.)

## 2. Objective & Scope
- Business/technical goals this standard enforces.
- Systems, environments, and data classifications in scope.

## 3. References
- Related PRDs/ADRs, compliance controls, regulatory mappings (e.g., SOC 2 CC, ISO 27001 Annex).
- Link to supporting threat models or risk assessments.

## 4. Policy Statements
_Describe the guardrails in plain language. Each statement should be testable._
1. ...
2. ...

## 5. Technical Requirements
| Control Area | Requirement | Verification Method |
| --- | --- | --- |
| Identity & Access | e.g., MFA required for all privileged roles | Azure AD policy report |
| Secrets Management | e.g., Managed identity only, no inline secrets | CI check, Key Vault audit |
| Network Security | | |
| Data Protection | | |
| Logging & Monitoring | | |

## 6. Specification by Example Scenarios
| Scenario | Given | When | Then | Automated? |
| --- | --- | --- | --- | --- |
| Unauthorized API call | ... | ... | ... | Yes/No |

## 7. Compliance & Auditing
- Evidence to collect (scan reports, policy exports, screenshots).
- Retention period and storage location.
- Responsible team for audits.

## 8. Exceptions Process
- How to request an exception (link to RFC issue template).
- Required information: risk, mitigation, expiration date.

## 9. Rollout Plan
- Phases (pilot, org-wide).
- Communication & training needs.
- Success metrics / KPIs.

## 10. Change Log
| Date | Author | Change | Approval |
| --- | --- | --- | --- |
