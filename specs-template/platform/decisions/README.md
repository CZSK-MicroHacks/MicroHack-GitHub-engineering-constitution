# Platform Architecture Decisions

This folder contains the "Constitution" of the platform—decisions that apply to **all services** or define the default standards for the organization.

## Scope
Decisions here typically cover:
- **Default Tech Stack**: "We use PostgreSQL for relational data."
- **Protocols**: "All synchronous APIs must use REST/JSON."
- **Security Standards**: "All services must validate JWTs from the central IDP."
- **Cross-Cutting Concerns**: Logging formats, error handling patterns, versioning strategies.

## Relationship to Service Decisions
Service-level decisions (`services/<name>/decisions/`) should reference these platform decisions when they are compliant, and **must explicitly justify** any deviation (exception) from these standards.

## Index
| ID | Title | Status | Date |
| --- | --- | --- | --- |
| 0000 | [ADR Template](./0000-template.md) | Active | 2023-01-01 |
