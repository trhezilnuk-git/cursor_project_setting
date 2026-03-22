# cursor_project_setting

Shared **Cursor**, **VS Code workspace**, and **Python tooling** files for multi-repo Python services. Paths match what Cursor uses when you open a project folder (repository root).

**한국어 단계별 설정:** [설정 가이드 (docs/설정_가이드.md)](docs/설정_가이드.md) — 처음부터 끝까지 따라 하면 적용이 완료되도록 정리했습니다.

## What is included

| Path | Purpose |
|------|---------|
| `.cursor/rules/*.mdc` | Cursor agent rules (team + Python) |
| `.cursorignore` | Exclude venv, caches, secrets from Cursor indexing |
| `.vscode/settings.json` | Format on save, Ruff, pytest |
| `.vscode/extensions.json` | Recommended extensions |
| `.editorconfig` / `.gitattributes` | Line endings and indentation |
| `pyproject.toml` | Ruff, pytest, mypy; replace placeholders for each service |
| `AGENTS.md` | High-level context for AI tools |
| `.python-version` | Suggested Python version (pyenv etc.) |

## Install into an existing repository

From the **root of your service repo** (the same folder you open in Cursor):

```bash
# Clone only the template files you need, or clone full repo to a temp dir and copy.
git clone --depth 1 https://github.com/trhezilnuk-git/cursor_project_setting.git /tmp/cursor_project_setting
cp -R /tmp/cursor_project_setting/.cursor .
cp -R /tmp/cursor_project_setting/.vscode .
cp /tmp/cursor_project_setting/.cursorignore .
cp /tmp/cursor_project_setting/.editorconfig .
cp /tmp/cursor_project_setting/.gitattributes .
cp /tmp/cursor_project_setting/.python-version .
cp /tmp/cursor_project_setting/pyproject.toml .
cp /tmp/cursor_project_setting/AGENTS.md .
# Optional: merge README; do not overwrite your service README blindly.
```

Then edit `pyproject.toml` (`name`, `packages`, `your_package`) and `AGENTS.md` for that service. Open the folder in Cursor; accept **recommended extensions** when prompted.

## Use as a new service template

```bash
git clone https://github.com/trhezilnuk-git/cursor_project_setting.git my-new-service
cd my-new-service
rm -rf .git
git init
# Rename src/your_package and update pyproject.toml + AGENTS.md
```

## Local setup

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -e ".[dev]"
ruff check . && ruff format . && pytest
```

## Python version

`.python-version` targets **3.12** for pyenv-style workflows. `pyproject.toml` sets `requires-python = ">=3.9"` so older laptops can still install dev tools; if your org standardizes on 3.12 only, change that field to `>=3.12` and align `tool.mypy.python_version`.

Fork or transfer the repository if your team uses a GitHub organization; update clone URLs accordingly.
