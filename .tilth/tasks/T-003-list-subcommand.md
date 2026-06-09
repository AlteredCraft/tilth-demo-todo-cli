---
id: T-003
title: Implement the `list` subcommand
---

## Description
Extend `todo_cli` so that `python3 -m todo_cli list` reads `TODOS.md` from the
current working directory and prints each item to **stdout**, one per line, with
a 1-based index: `N. [ ] text` for open items and `N. [x] text` for done items,
preserving the order they appear in the file.

When `TODOS.md` is missing, or exists but contains no lines matching the item
format (`- [ ] ` / `- [x] ` prefix), print exactly `(no todos)` followed by a
newline to stdout and exit 0. Lines that don't match the item format are ignored
on read (they don't count toward the index and don't appear in the output).

## Acceptance criteria
- With a `TODOS.md` containing two items, `list` prints them to stdout with 1-based indices in the original file order (e.g. `1. [ ] buy milk` then `2. [x] call mom`) and exits 0.
- With `TODOS.md` missing, `list` prints exactly `(no todos)\n` to stdout and exits 0.
- With `TODOS.md` present but containing no lines matching the item format, `list` prints exactly `(no todos)\n` and exits 0.
