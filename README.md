# cursor_project_setting

Shared **Cursor**, **VS Code workspace**, and **Python tooling** files for multi-repo Python services. Paths match what Cursor uses when you open a project folder (repository root).

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
git clone --depth 1 https://github.com/YOUR_ORG/cursor_project_setting.git /tmp/cursor_project_setting
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
git clone https://github.com/YOUR_ORG/cursor_project_setting.git my-new-service
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

Replace `YOUR_ORG` in the clone URL after this repository is published under your GitHub user or organization.
