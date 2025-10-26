Overview

This repository contains two distinct sets of tests:

- Core tests: validate Flask’s internal APIs and behavior, located in the top-level `tests/` directory.
- Example app tests: validate the tutorial and patterns repositories under `examples/`, each with its own `tests/` directory and local config.

Core tests (repository root)

The root `pyproject.toml` is configured to run only the core test suite (via `tool.pytest.testpaths = ["tests"]`). Example app tests are not included when you run pytest from the repository root.

Run core tests with pytest:

1. Create and activate a virtual environment.
   - Linux/macOS:
     - `python -m venv .venv && . .venv/bin/activate`
   - Windows (PowerShell):
     - `python -m venv .venv; .venv\\Scripts\\Activate.ps1`
2. Install Flask and the test dependencies.
   - `pip install -e .`
   - `pip install pytest python-dotenv greenlet asgiref`
3. Run the test suite from the repository root.
   - `pytest -v --tb=short`

Alternatively, use tox to exercise multiple environments:

- `tox -e py3.13` (run core tests under Python 3.13)
- `tox -e tests-min` (run core tests against minimum dependency versions)
- `tox -e tests-dev` (run core tests against development versions of dependencies)

Example app tests (under examples/)

Each example app has its own `pyproject.toml` and test settings. To run tests for an example, change into that example’s directory and use its configuration.

Tutorial app (`examples/tutorial`):

1. `cd examples/tutorial`
2. Create and activate a virtual environment.
   - `python -m venv .venv && . .venv/bin/activate`
3. Install the app and its test extras.
   - `pip install -e .[test]`
4. Run tests.
   - `pytest -v --tb=short`

JavaScript patterns app (`examples/javascript`):

1. `cd examples/javascript`
2. Create and activate a virtual environment.
   - `python -m venv .venv && . .venv/bin/activate`
3. Install the app and its test extras.
   - `pip install -e .[test]`
4. Run tests.
   - `pytest -v --tb=short`

Notes and tips

- Separation: Running `pytest` from the repository root only executes core tests in `tests/`. Example app tests must be run from their respective example directories.
- Selecting tests: Use `pytest -k <expr>` to filter tests (for example, `pytest -k templating`).
- Coverage: For core tests, coverage is configured in the root `pyproject.toml`. For example apps, coverage is configured in each example’s `pyproject.toml`.
- Environments: If you use tox, see `pyproject.toml` under `[tool.tox.env.*]` for available environments.

