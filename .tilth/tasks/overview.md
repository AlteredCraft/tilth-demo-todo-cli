# Markdown-backed todo CLI

## Goal
Build a small command-line todo tool, `todo_cli`, that stores its items in a
plain-text `TODOS.md` file in the current working directory. A user can add
items, list them, and mark them done. The on-disk format is human-readable
markdown checkboxes, so the file stays useful even without the tool.

## Context
- This is a greenfield Python 3.12 package — there is no `todo_cli/` yet. Build
  it under `todo_cli/` with a `__main__.py` so `python3 -m todo_cli ...` works.
- Storage is a single `TODOS.md` in the process's current working directory. The
  line format is the contract every subcommand shares:
  - open item:  `- [ ] <text>`
  - done item:  `- [x] <text>`
  One item per line; order in the file is the order the user sees.
- Conventions live in `AGENTS.md`: standard-library only (no third-party runtime
  deps), type-annotate public functions, no global state outside `__main__`.

## Scope boundaries
- **In scope:** the `todo_cli` package scaffold and the `add`, `list`, and `done`
  subcommands, each with the error/exit-code behaviour its task spells out.
- **Out of scope:** a `remove` subcommand (the usage line advertises it, but it
  is a later task — do not implement it), priorities, due dates, tags, an
  interactive mode, config files, or any storage format other than `TODOS.md`.
  Don't add third-party dependencies.

## Notes for the reviewer
- The `TODOS.md` line format is the load-bearing contract — every subcommand reads
  and writes it, so a deviation in one task breaks the next.
- `done` must be idempotent: marking an already-done item leaves the file byte-for-byte
  unchanged and still exits 0.
- Error paths (missing argument, bad index) print a usage line to **stderr** and exit 2;
  success exits 0. These exact codes are what the acceptance criteria check.
