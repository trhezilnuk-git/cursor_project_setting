# Agent / AI context

Short project facts for Cursor and other AI tools. **Edit per service repository.**

## Stack

- Language: Python 3.12+ in CI/production; `pyproject.toml` may allow a lower minimum for developer machines—align with your org.
- Layout: `src/` package layout (adjust if your team uses flat layout).

## Commands (after `pip install -e ".[dev]"` or equivalent)

- Lint/format: `ruff check .` and `ruff format .`
- Types: `mypy src`
- Tests: `pytest`

## Conventions

- Follow `.cursor/rules/` and team docs for security and review expectations.
- Prefer English for code symbols; team language for comments is a team policy decision.
