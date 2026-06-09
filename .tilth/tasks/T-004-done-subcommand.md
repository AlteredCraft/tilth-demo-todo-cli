---
id: T-004
title: Implement the `done` subcommand
---

## Description
Extend `todo_cli` so that `python3 -m todo_cli done <index>` marks the 1-based
item at `<index>` in `TODOS.md` as done by flipping its `- [ ]` prefix to
`- [x]`. Only that item changes; no other item is reordered or modified, and the
rest of each line's text is preserved exactly.

The operation is idempotent: running `done` on an item that is already `- [x]`
leaves the file byte-for-byte unchanged and exits 0. With no index, a
non-integer index, or an index out of range — including any index when
`TODOS.md` is missing — print a usage line to **stderr** and exit 2 without
modifying the file.

The index counts only valid item lines (the same lines `list` would number), in
file order.

## Acceptance criteria
- With a `TODOS.md` containing two open items, `done 1` flips the first item to `- [x]`, leaves the second item untouched, and exits 0.
- Running `done <n>` on an item that is already marked done leaves the file byte-for-byte unchanged and exits 0.
- Running `done` with no index, with a non-integer index, or with an out-of-range index (including when `TODOS.md` is missing) prints a usage line to stderr, leaves any existing file unchanged, and exits 2.
