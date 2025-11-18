# Python Engineering Standard

## 1. Scope
Applies to all Python services, data scripts, and AI agents maintained by MicroHack teams, including FastAPI backends and automation tooling.

## 2. Language & Style
- Target **Python 3.11+** for new projects; do not introduce code that requires deprecated versions.
- Follow **PEP 8** with these clarifications:
  - Max line length 100 characters.
  - Prefer `snake_case` for functions/variables, `PascalCase` for classes.
  - Use **type hints everywhere**; enforce via `mypy` or `pyright` CI checks.
- Document every public function/class with docstrings describing purpose, parameters, returns, and exceptions.

## 3. Project Layout
```
app/
  __init__.py
  routes/
  services/
  repositories/
  models/
  schemas/
 tests/
 docs/
```
- `models/` contains Pydantic schemas shared across routes/services.
- Keep infrastructure code (infra as code, scripts) in dedicated folders to avoid polluting application packages.

## 4. Dependencies & Packaging
- Use `uv` with `pyproject.toml` as the single dependency manifest; avoid `requirements.txt` unless exporting for third-party needs.
- Pin indirect dependencies via `uv lock` to ensure repeatable builds.
- Prohibit unmaintained or unlicensed packages; security reviews run via `pip-audit` or `safety`.

## 5. Logging & Observability
- Use the standard `logging` library with structured log adapters (JSON when running in Kubernetes or Functions).
- No `print` statements in production code.
- Log at INFO for lifecycle events, DEBUG for diagnostics, WARNING for recoverable anomalies, ERROR for failures.

## 6. Error Handling & Resilience
- Bubble validation errors with meaningful messages; prefer custom exception classes over raw `ValueError`.
- Wrap external IO (DB, HTTP, queues) with retry-capable clients. Include exponential backoff and jitter for transient failures.
- For Azure Cosmos DB usage, reuse a singleton `CosmosClient`, honor `Retry-After` headers, and log diagnostics when latency or status codes deviate from expectations.

## 7. Testing
- Use `pytest` with descriptive test names (`test_<function>_<behavior>`).
- Keep unit tests fast and free of live IO; mock repositories/interfaces.
- Provide integration tests for persistence layers and API contracts; run them nightly or per-merge when feasible.
- Ensure Specification by Example scenarios exist as automated tests before implementing major behavior.

## 8. Security
- Load secrets from managed stores (Key Vault, secrets manager). Never commit credentials.
- Enforce dependency scanning and formatting in CI: `ruff`, `mypy`, `pytest`, `pip-audit` (or equivalent) must pass before merge.
- Validate all untrusted inputs via Pydantic models before use.

## 9. Performance & Resource Management
- Use async FastAPI routes unless blocked by CPU-bound work; offload heavy CPU tasks to background workers or concurrency-friendly executors.
- Close DB/network connections gracefully via context managers or dependency injection lifecycles.

## 10. Documentation
- Keep `docs/` (REQUIREMENTS, DESIGN, DATA_MODELS, API_REFERENCE) updated as part of PRs.
- Include run/test instructions in the service-level `README.md`.
- Log architectural decisions in `docs/IMPLEMENTATION_LOG.md` immediately after merging.
