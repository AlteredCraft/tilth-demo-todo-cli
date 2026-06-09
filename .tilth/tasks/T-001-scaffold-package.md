---
id: T-001
title: Scaffold the todo_cli package with a usage entrypoint
---

## Description
Create a `todo_cli/` package with `__init__.py` and `__main__.py`. In
`todo_cli/__main__.py`, define a `main()` function that, when called with no
arguments, prints the usage line `usage: todo [add|list|done|remove]` to
**stderr** and exits with code 2. Wire it up so `python3 -m todo_cli` invokes
`main()`.

This is the scaffold every later subcommand builds on — keep it minimal. Do not
implement any subcommand behaviour yet; an unknown or missing subcommand should
fall through to the same usage line + exit 2.

## Acceptance criteria
- The directory `todo_cli/` exists with `__init__.py` and `__main__.py`.
- Running `python3 -m todo_cli` with no arguments prints `usage: todo [add|list|done|remove]` to stderr and exits with code 2.
- Running `python3 -c "import todo_cli; print(todo_cli.__name__)"` prints `todo_cli` and exits 0.
