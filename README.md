# MicroHack GitHub Engineering Constitution

This repository is the shared source of truth for engineering governance across all MicroHack projects. It captures our constitution, governance workflow, contribution expectations, technical standards, and reusable templates so that every new service starts from the same spec-driven baseline.

## Why this repo exists
- **Single reference**: consolidate principles, policies, and templates that every team can trust.
- **Spec-driven development**: every change starts from written specifications (`docs/`, standards, templates) so implementation always traces back to intent. The Specification by Example mindset (concrete user-facing examples, living documentation, shared ownership) keeps specs and code evolving together.
- **Frictionless reuse**: teams can copy/paste vetted templates and adapt standards without reinventing process.

## Repository map
| Path | Purpose |
| --- | --- |
| `CONSTITUTION.md` | Core principles, decision guardrails, and change-management expectations. |
| `GOVERNANCE.md` | Roles, RACI, RFC flow, and approval requirements. |
| `CONTRIBUTING.md` | How to propose updates, add standards/templates, and reference implementation evidence. |
| `standards/` | Language- or domain-specific expectations (Python, TypeScript, security, testing). |
| `templates/` | Ready-to-use scaffolds for ADRs, PRDs, security checklists, and coding guidelines. |
| `specs-template/` | Full specification workspace skeleton; copy this entire folder into your repo (typically as `docs/specs/`) to bootstrap multi-file specs. |

> `templates/` hosts individual markdown scaffolds you copy per document, while `specs-template/` is the complete multi-file workspace that keeps those documents organized. Keep both names—they signal the scope of assets you are copying.

## How to use this repo
1. **Start every initiative here**: review the constitution and governance docs, then select relevant templates before drafting specs in your service repository.
2. **Create or update specs first**: copy `specs-template/` (or use the instructions in `templates/specs-template.md`) into your repo, then follow the spec-driven workflow (`docs/REQUIREMENTS.md`, `docs/DESIGN.md`, etc.) to keep stakeholder-approved examples alongside requirements.
3. **Adopt standards as guardrails**: each standards file lists mandatory and optional guidance. Reference them in your service-specific docs so variance stays intentional.
4. **Propose improvements via RFCs**: use the governance workflow to introduce new standards, templates, or constitutional changes. Document context, options, decision, and verification plan.

## Spec-driven workflow essentials
- **Specification by Example**: capture requirements as concrete scenarios that double as acceptance tests and documentation, ensuring shared understanding across product, engineering, and QA.
- **Living documentation**: keep specs versioned with code. When behavior changes, update both the standard/template and downstream service docs.
- **Traceability**: link PRs, ADRs, and PRDs back to governance artifacts for auditability.

## Contributing at a glance
- Discuss large changes with stakeholders early and log rationale in `docs/IMPLEMENTATION_LOG.md` of the consuming repo.
- Follow the RFC checklist in `GOVERNANCE.md` before merging constitution or standard updates.
- Use the templates in `templates/` as starting points; never edit them in-place for project-specific needs—copy them into your service repo.

Refer to `CONSTITUTION.md`, `GOVERNANCE.md`, and `CONTRIBUTING.md` for the authoritative rules and workflows.