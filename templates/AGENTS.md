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
* Primary documentation channel inside code: **docstrings** (revise them whenever code changes behavior or signature).
* Only add code comments for non‑obvious logic or critical nuances. Never for progress logs, migration notes, or “previous implementation” commentary.
* Update `specs/IMPLEMENTATION_LOG.md` with meaningful architectural or technical decisions (not micro‑steps) when a feature is completed or a design choice is finalized.
* Add confirmed recurring pitfalls to `specs/COMMON_ERRORS.md` (after user confirmation—see Section 6).
* Each component/service keeps concise run & test instructions in its local `README.md`.

### 3.2 Refactoring & Improvements
Opportunistic simplifications are encouraged. When you see a refactor beyond the immediate task:
* Perform low‑risk, obviously beneficial cleanups directly (pure simplification, dead code removal).
* For broader architectural shifts, surface a brief rationale in chat before proceeding.

### 3.3 Experiments & Troubleshooting
[Define experiments and troubleshooting strategy for agent]

### 3.4 Technology Stack
* [Define Primary Language & Package Management]
* [Define API Framework]
* [Define Data Validation Strategy]
* [Define Frontend Stack if applicable]

## 4. Service Guidelines

### 4.1 Structure & Modeling
* Keep service boundaries explicit (e.g., `routes/`, `services/`, `repositories/`).
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

## 6. Reinforced Documentation & Logging Rules (Augmented Requirements)

These constraints exist to prevent uncontrolled documentation sprawl and progress leakage into code:

1. Implementation Log Boundaries: Implementation progress, rationale, or “this replaces X” notes belong in `specs/IMPLEMENTATION_LOG.md`—never as inline code comments or new files.
2. Common Errors Workflow: Only after confirming with the user that an issue is broadly relevant, add it to `specs/COMMON_ERRORS.md`. Do not create parallel error collections.
3. Controlled Design Changes: Architectural or behavioral design alterations should be reflected (after approval) in `specs/` documentation. Treat specs as guiding artifacts; do not mutate them unilaterally.
4. New Doc File Exception: If a truly new doc artifact is justified, prefix filename with `ADHOC_` and notify user. Expect eventual consolidation or deletion.
5. No Progress/History Comments: Ban inline comments like “// updated previous logic” or “# temporary hack (will remove)” — instead record durable decisions in `specs/IMPLEMENTATION_LOG.md`.

## 7. Ad‑Hoc / Disposable Artifacts

| Type | Naming Pattern | Purpose | Lifecycle |
|------|----------------|---------|-----------|
| Scratch test script | `adhoc_test_*` or `adhoc_*` | Quick reproduction / isolate behavior | Delete after converting insight into real tests/code |
| Documentation draft | `ADHOC_*.md` | Rare: staging ground for large doc refactor | Merge content into canonical doc then delete |

Rules:
* Must not be imported by production code.
* Must not hold secrets or credentials.
* Track none of them in long‑term design history; only distilled results.

## 8. Change Control & Communication

1. Before major architectural changes: summarize intent, risk, alternatives in chat for approval.
2. After implementing a feature: update relevant docstrings + (if needed) `specs/IMPLEMENTATION_LOG.md`.
3. If you discover systemic flaw: propose remediation path; avoid broad speculative refactors without confirmation.

## 9. Quick Reference Checklist

[Define Development Flow for agent to follow]

## 10. Scope & Precedence

This `AGENTS.md` centralizes operational & stylistic guidance. If conflicts arise:
1. Explicit user instruction (chat) overrides this file case‑by‑case.
2. `specs/` documentation governs architecture (pending approved changes).
3. This file governs daily engineering discipline & hygiene.
