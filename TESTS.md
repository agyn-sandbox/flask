Prerequisites:
- Python >= 3.10
- pip
- Dependencies: pytest (and dev/test group extras)

Setup:
- pip install -e .
- pip install -r pyproject.toml groups: tests (or install pytest directly)

Run tests:
- pytest -v --tb=short

Troubleshooting:
- Ensure Werkzeug and click compatible versions.
