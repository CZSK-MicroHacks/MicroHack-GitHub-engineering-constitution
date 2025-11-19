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
.
├── main.py           # Application entry point and route definitions
├── models.py         # Pydantic models and schemas
├── database.py       # Database service layer and connection logic
├── config.py         # Configuration and environment variable handling
├── requirements.txt  # Python dependencies
├── start.sh          # Startup and setup script
├── Dockerfile        # Container definition
└── tests/            # Test files (e.g., test_main.py)
```
- Use a flat structure for microservices to reduce complexity.
- `models.py` contains Pydantic schemas.
- `database.py` encapsulates all database logic (connection, CRUD, queries).
- `config.py` manages environment variables and application settings.

## 4. Dependencies & Packaging
- Use `pip` with `requirements.txt` for dependency management.
- Use standard `venv` for virtual environments.
- Include a `start.sh` script to automate environment setup, virtual env creation, and dependency installation.
- Pin dependencies in `requirements.txt` to ensure repeatable builds.

## 5. Logging & Observability
- Use the standard `logging` library configured in `main.py`.
- No `print` statements in production code; use `logger.info()`, `logger.error()`, etc.
- Log at INFO for lifecycle events, DEBUG for diagnostics, WARNING for recoverable anomalies, ERROR for failures.

## 6. Error Handling & Resilience
- Use FastAPI's `HTTPException` for API errors with appropriate status codes.
- Bubble validation errors with meaningful messages.
- Wrap external IO (DB, HTTP, queues) with retry-capable clients. Include exponential backoff and jitter for transient failures.
- For Azure Cosmos DB usage, reuse a singleton `CosmosClient`, honor `Retry-After` headers, and log diagnostics when latency or status codes deviate from expectations.

## 7. Testing
- Use `pytest` with descriptive test names (`test_<function>_<behavior>`).
- Keep unit tests fast and free of live IO; mock repositories/interfaces.
- Provide integration tests for persistence layers and API contracts; run them nightly or per-merge when feasible.
- Ensure Specification by Example scenarios exist as automated tests before implementing major behavior.

## 8. Security
- Load secrets from environment variables using `.env` files (local) or managed identity (cloud).
- Use `.env.example` to document required environment variables without committing secrets.
- Enforce dependency scanning and formatting in CI: `ruff`, `mypy`, `pytest`, `pip-audit` (or equivalent) must pass before merge.
- Validate all untrusted inputs via Pydantic models before use.

## 9. Performance & Resource Management
- Use async FastAPI routes unless blocked by CPU-bound work; offload heavy CPU tasks to background workers or concurrency-friendly executors.
- Close DB/network connections gracefully via context managers or dependency injection lifecycles.

## 10. Documentation
- Keep `docs/` (REQUIREMENTS, DESIGN, DATA_MODELS, API_REFERENCE) updated as part of PRs.
- Include run/test instructions in the service-level `README.md`.
- Log architectural decisions in `docs/IMPLEMENTATION_LOG.md` immediately after merging.
