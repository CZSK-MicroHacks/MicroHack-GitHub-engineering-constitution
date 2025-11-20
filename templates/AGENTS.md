# Agent Development Guidelines

## 1. Purpose

Provide a clear, single reference for implementing, extending, and maintaining AI agents and related services in this repository.

## 2. Core Principles

1. Favor simplicity and readability over premature abstraction.
2. Keep functionality self‑documenting; use docstrings, not progress/status comments.
3. Minimize surface area: small, cohesive modules > large monoliths.
4. Explicit > implicit for data contracts, configuration, and side effects.
5. Make cheap experiments disposable (prefixed `adhoc_`), not permanent.

## 3. Project‑Wide Conventions

### 3.1 Documentation
* **Specs Structure**:
    * `specs/platform/`: Cross-cutting concerns (Architecture, Data Models, Security).
    * `specs/platform/decisions/`: Project-wide Architecture Decision Records (ADRs).
    * `specs/services/<service>/`: Service-specific specs (API, Testing, Deployment).
    * `specs/services/<service>/decisions/`: Service-specific ADRs.
* Primary documentation channel inside code: **docstrings** (revise them whenever code changes behavior or signature).
* Only add code comments for non‑obvious logic or critical nuances. Never for progress logs, migration notes, or “previous implementation” commentary.
* **Implementation Details**: Update `docs/IMPLEMENTATION_LOG.md` autonomously with meaningful technical decisions (e.g., "Switched to library X for performance", "Refactored auth flow"). Do not ask for permission for these logs.
* **Architecture Decisions**: For fundamental changes (e.g., "Adding a new database", "Changing API protocol"), **propose** an ADR (Architecture Decision Record). Prepare a draft for user review, but **never** create/merge it autonomously.
* Add confirmed recurring pitfalls to `docs/COMMON_ERRORS.md` (after user confirmation—see Section 6).
* Each component/service keeps concise run & test instructions in its local `README.md`.

### 3.2 Refactoring & Improvements
Opportunistic simplifications are encouraged. When you see a refactor beyond the immediate task:
* Perform low‑risk, obviously beneficial cleanups directly (pure simplification, dead code removal).
* For broader architectural shifts, surface a brief rationale in chat before proceeding.

### 3.3 Experiments & Troubleshooting
* **Consult First**: Always check `docs/COMMON_ERRORS.md` before starting deep troubleshooting.
* **Propose Additions**: After fixing a non-trivial error, actively recommend adding it to `docs/COMMON_ERRORS.md`.
    *   Draft the entry (Error, Cause, Fix).
    *   Show it to the user.
    *   **Wait for approval** before writing to the file.

### 3.4 Technology Stack
* [Define Primary Language & Package Management]
* [Define API Framework]
* [Define Data Validation Strategy]
* [Define Frontend Stack if applicable]

## 4. Service Guidelines

### 4.1 Structure & Modeling
* [Define Modeling Strategy]

### 4.2 Documentation & Style
* Every public class/function: docstring specifying purpose, parameters, return value(s), exceptions.
* Avoid redundant comments explaining obvious code or restating names.
* [More documentation instructions]

### 4.3 Logging
* Use appropriate logging levels: DEBUG (diagnostics), INFO (lifecycle events), WARNING (recoverable anomalies), ERROR (failures), CRITICAL (systemic outages).
* [More logging instructions]

### 4.4 Testing
* [Define Testing Framework]
* Prefer unit tests (mocks) for logic; integration tests for IO (DB, external HTTP, vector stores, etc.).
* If a one‑off exploratory script was needed, port validated findings into tests and delete the ad‑hoc script.

## 5. Infrastructure as Code (Optional)

* [Define IaC Providers]
* [Define File Organization]
* [Define Variable Standards]

## 6. Reinforced Documentation & Logging Rules

These constraints exist to prevent uncontrolled documentation sprawl and progress leakage into code:

1. Implementation Log Boundaries: Implementation progress and technical details belong in `docs/IMPLEMENTATION_LOG.md`. Update this file autonomously as you work.
2. Architecture Decision Boundaries: Fundamental changes require an ADR. **Never** write an ADR autonomously. Always propose the content and wait for user review.
3. Common Errors Workflow:
    *   Consult `docs/COMMON_ERRORS.md` when stuck.
    *   After fixing, **propose** the addition to the user.
    *   Only write to the file after explicit user approval.
4. Controlled Design Changes: Architectural or behavioral design alterations should be reflected (after approval) in `specs/` documentation. Treat specs as guiding artifacts; do not mutate them unilaterally.
4. New Doc File Exception: If a truly new doc artifact is justified, create it in `docs/` with prefix `ADHOC_` and notify user. Expect eventual consolidation or deletion.
5. No Progress/History Comments: Ban inline comments like “// updated previous logic” or “# temporary hack (will remove)” — instead record durable decisions in `docs/IMPLEMENTATION_LOG.md`.

## 7. Ad‑Hoc / Disposable Artifacts

| Type | Naming Pattern | Purpose | Lifecycle |
|------|----------------|---------|-----------|
| Scratch test script | `adhoc_test_*` or `adhoc_*` | Quick reproduction / isolate behavior | Delete after converting insight into real tests/code |
| Documentation draft | `docs/ADHOC_*.md` | Rare: staging ground for large doc refactor | Merge content into canonical doc then delete |

Rules:
* Must not be imported by production code.
* Must not hold secrets or credentials.
* Track none of them in long‑term design history; only distilled results.

## 8. Change Control & Communication

1. Before major architectural changes: summarize intent, risk, and alternatives in chat. If agreed, **propose an ADR draft** for review.
2. After implementing a feature: update relevant docstrings + (if needed) `docs/IMPLEMENTATION_LOG.md`.
3. If you discover systemic flaw: propose remediation path; avoid broad speculative refactors without confirmation.

## 9. Quick Reference Checklist

[Define Development Flow for agent to follow]

## 10. Scope & Precedence

This `AGENTS.md` centralizes operational & stylistic guidance. If conflicts arise:
1. Explicit user instruction (chat) overrides this file case‑by‑case.
2. `specs/` documentation governs architecture (pending approved changes).
3. This file governs daily engineering discipline & hygiene.
