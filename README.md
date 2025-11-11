# Flask Starter Template 🚀

A ready-to-use **Flask project template** for quickly starting new Flask apps.  
Includes a basic app structure, templates, static files, testing setup, and environment examples.

---

## 📁 Project Structure

```
app/
├── init.py # Initialize Flask app
├── routes.py # Define routes/views
├── models.py # Define models (optional)
├── templates/ # HTML templates (Jinja2)
├── static/ # Static files (CSS, JS, images)
tests/
├── test_basic.py # Basic example test
root/
├── pyproject.toml 
├── Dockerfile
├── .dockerignore
├── pyproject.toml 
```

---

## ⚙️ Setup & Installation

### 1. Clone a new project from this template
Click **“Use this template” → “Create a new repository”** at the top of this page.

*The remaining steps still be done on your new repository*
### 2. Setup `pyproject.toml`
```ini
[project]
name = ""
version = ""
description = ""
readme = ""
requires-python = ""
license = {text = ""}
authors = [{ name = "" }]
# keep small
dependencies = [
  "",
  "",
]

[project.optional-dependencies]
dev = [
  "pytest",
  "pytest-cov",
  "black",
  "ruff",
  "pre-commit",
  "httpx",  # needed for fastapi.testclient module
  "<insert>",           #insert your packages here, comma separated
  "<insert>"           
]

[tool.black]
line-length = 100
target-version = ["py311"]
exclude = '/(\.venv|build|dist|.history)/'  # exclude must be a string

[tool.ruff]
line-length = 100
target-version = "py311"
# Pick a sane set; you can expand later
select = ["E", "F", "W", "I"]  # pycodestyle, pyflakes, warnings, isort
ignore = ["E501"]              # black handles line length
exclude = [".venv", "build", "dist", ".history"]


[tool.ruff.format]
quote-style = "double"

[tool.pytest.ini_options]

# Optional strict typing (if you use mypy)
[tool.mypy]
```

### 3. Set up your environment

```bash
python3 -m venv venv && source .venv/bin/activate
pip install -e ".[dev]"
pip freeze --exclude-editable  > requirements.txt
```
### 4. Setup `pytest.imi`
```ini
[pytest]
testpaths = tests
python_files = test_*.py
addopts = --maxfail=1 -q
```

### 5. Setup `black` 
enforces consistent formatting
```bash
# command line
black .
# CI run
black --check .
```

### 6. Setup `Ruff`
Ruff is a linter and code fixer for Python written in Rust (blazing fast). It checks your code against hundreds of rule families—for syntax errors, bad patterns, style issues, import order, etc.—and can auto-fix many of them.
- Configure Ruff inside your pyproject.toml It sets defaults so you (and CI) can just run ruff check . without flags.
```bash
ruff check .  # Lint Check (Only)
ruff check . -- fix # Auto Fix
ruff format . # CLI format
ruff check . --exit-zero  # always passes (for exploratory)
ruff check . --output-format=github  # nice PR comments
```

### 7. Add black and ruff to pre-commit hook locally
1. Add `pre-commit-config.yaml`
> It's currently using python version 3.10 but you can change to whatever you like. I'd also make sure you are using the most up to date versions below. This is just a template.
```ini
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.6.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-yaml
      - id: check-toml
      - id: mixed-line-ending

  - repo: https://github.com/astral-sh/ruff-pre-commit
    rev: v0.6.9
    hooks:
      - id: ruff
        args: [--fix]

  - repo: https://github.com/psf/black
    rev: 24.10.0
    hooks:
      - id: black
        language_version: python3.10
```
1. Install + enable (fish shell)
```bash
source .venv/bin/activate.fish
pip install pre-commit
pre-commit install           # installs the git hook
pre-commit run --all-files   # run once across the whole repo
```

## 8. Enjoy, :)!
