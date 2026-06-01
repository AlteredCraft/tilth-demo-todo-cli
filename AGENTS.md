# AGENTS.md — todo-cli

Seeded conventions for the todo-cli demo project.

## Project

A small markdown-backed TODO CLI.

## Language and tooling

- Python 3.12 (use `uv` to init, manage virtual environments, and dependencies).
- Test framework: `pytest`
- Formatter / linter: `ruff` (default config)
- No external runtime dependencies for the CLI itself unless a task says otherwise.

## Layout

- `todo_cli/` — package directory.
- `tests/` — acceptance tests, mirror of the package layout.

## Style

- Standard library first; pull in third-party deps only when a task explicitly requires it.
- Type-annotate public functions.
- No global state outside `__main__` blocks.

