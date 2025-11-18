# Contributing Guidelines

Thank you for strengthening the MicroHack engineering constitution. Contributions should keep our standards actionable, testable, and spec-driven.

## 1. Before You Propose a Change
- Review `README.md`, `CONSTITUTION.md`, and `GOVERNANCE.md` to ensure your idea aligns with our principles.
- Check open RFCs or issues to avoid duplicate efforts.
- Gather evidence: user research, incident data, benchmark results, or reference implementations.

## 2. Choosing the Right Artifact
| Scenario | Artifact |
| --- | --- |
| New/updated policy or principle | Amend `CONSTITUTION.md` via RFC |
| Process or approval workflow | Update `GOVERNANCE.md` |
| How-to for potential contributors | Update this file |
| Language/test/security expectation | Update relevant file in `standards/` |
| New reusable document scaffold | Add or modify a file in `templates/` |

## 3. Workflow
1. **Open an Issue** describing the problem, scope, and urgency.
2. **Draft an RFC** (ADR template or repository issue) for constitutional, governance, or cross-team standard changes.
3. **Discuss Early** with Architecture Council, Security Lead, and affected service owners.
4. **Update Artifacts**: edit markdown files using concise language, tables, and checklists. Add comments only when logic is non-obvious; rely on doctexts for everything else.
5. **Link Evidence**: cite experiment logs, implementation log entries, or upstream repository commits validating the change.
6. **Request Reviews** per the RACI table. At least one AC member must approve standards or templates.
7. **Merge & Announce** in #engineering-gov with effective date and rollout instructions.

## 4. Style & Quality Checklist
- Prefer active voice and short sentences.
- Reference Specification by Example practices where applicable (e.g., include sample scenarios for new standards).
- Use numbered steps for procedures, tables for matrices, and checklists for verification tasks.
- Keep markdown ASCII-only unless a domain-specific symbol is required.
- When adding links to external references, prefer authoritative sources (standards bodies, official docs).

## 5. Maintaining Templates
- Never edit templates for one-off needs; copy them into the target repo and modify locally.
- When improving a template, include a "How to customize" section so teams know what is optional vs. required.
- Ensure placeholders are descriptive (e.g., `<Describe user benefit>` instead of `TBD`).

## 6. After Merging
- Update onboarding materials or runbooks if the change affects daily workflows.
- Monitor downstream repositories for adoption; collect feedback during the next governance sync.
- If the change introduces new metrics or audit requirements, ensure tooling captures the data before the effective date.

By following these steps we keep the constitution a living, trustworthy resource for every MicroHack team.
