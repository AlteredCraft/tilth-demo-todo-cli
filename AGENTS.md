# AGENTS.md — todo-cli

Seeded conventions for the todo-cli demo project. The agent appends learnings here as it works.

## Project

A small markdown-backed TODO CLI built incrementally from `prd.json`. Each task in the PRD has explicit acceptance criteria and acceptance tests under `tests/`.

## Language and tooling

- Python 3.12
- Test framework: `pytest`
- Formatter / linter: `ruff` (default config)
- No external runtime dependencies for the CLI itself unless a task says otherwise.

## Layout

- `hello.py` — slice-1 sentinel script (created by T-001).
- `todo_cli/` — package directory (created by later tasks).
- `tests/` — acceptance tests, mirror of the package layout.

## Style

- Standard library first; pull in third-party deps only when a task explicitly requires it.
- Type-annotate public functions.
- No global state outside `__main__` blocks.

