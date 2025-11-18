# Governance & Decision-Making

## 1. Roles & Responsibilities
| Role | Core Responsibilities |
| --- | --- |
| **Architecture Council (AC)** | Custodians of the constitution and standards. Approve RFCs impacting multi-team architecture, security posture, or compliance.|
| **Product Steering Group (PSG)** | Prioritizes initiatives, resolves product-level trade-offs, validates PRDs and success metrics.|
| **Security Lead** | Reviews security standards, threat models, and exception requests.|
| **DevEx Lead** | Ensures tooling, CI/CD, and developer experience conform to standards; drives automation for guardrails.|
| **Project/Service Owner** | Maintains local repository docs, runs RFCs for service-scoped changes, enforces testing/quality gates.|
| **Contributors** | Propose improvements, follow templates, keep specs current, surface risks early.|

## 2. RACI Overview
| Decision Area | Responsible | Accountable | Consulted | Informed |
| --- | --- | --- | --- | --- |
| Amend Constitution | Project Owner drafting RFC | Architecture Council | Security Lead, PSG | All teams |
| Add/Update Standards | Standard Author | Architecture Council | Security Lead, DevEx | All teams |
| Template Changes | Template Author | DevEx Lead | Architecture Council, PSG | All teams |
| Service-specific ADR | Service Owner | Service Owner | AC delegate, Security Lead (if relevant) | PSG |
| Incident Postmortem Actions | Incident Commander | Incident Commander | AC, Security Lead, PSG | Engineering org |

## 3. RFC Workflow
1. **Problem Framing** – Use the ADR or RFC template to describe context, anti-goals, and success measures.
2. **Stakeholder Mapping** – Identify impacted teams and tag them in the discussion thread or issue tracker.
3. **Evidence Gathering** – Reference requirements, user research, architecture diagrams, threat models, or experiments.
4. **Review Window** – Minimum 5 business days; urgent exceptions require AC approval.
5. **Decision Recording** – Capture chosen option, rationale, dissenting opinions, and follow-up tasks. Commit RFCs to version control.
6. **Implementation Plan** – Map work to `docs/IMPLEMENTATION.md` checklists and assign owners.
7. **Verification** – Document test strategy, rollout plan, and metrics to monitor post-change.

## 4. Meeting Cadence
- **Bi-weekly Architecture Council**: review open RFCs, standards debt, pending exceptions.
- **Monthly Governance Sync**: PSG, AC, Security, DevEx to check roadmap alignment and audit status.
- **Quarterly Retro**: evaluate how well spec-driven development and Specification by Example practices are being followed; adjust training/onboarding as needed.

## 5. Exception Handling
- Submit exception requests via RFC template with risk assessment and mitigation timeline.
- Exceptions are granted for a fixed duration (default: 90 days) and tracked in the governance backlog.
- The Security Lead and AC review expiring exceptions and either close or extend with justification.

## 6. Tooling Expectations
- Use shared templates for RFCs, ADRs, PRDs, and security reviews to preserve consistency.
- Store discussions in GitHub Issues/PRs or approved knowledge bases to keep artifacts discoverable.
- Automate voting or approval gates via GitHub checks when feasible.

## 7. Transparency
- All governance artifacts reside in this repo or linked public spaces accessible to the engineering org.
- Summaries of approved RFCs are posted in #engineering-gov with links to evidence bundles and rollout timelines.
- Implementation outcomes (success metrics, learnings) are appended to the original RFC thread.
