---
id: T-002
title: Implement the `add` subcommand
---

## Description
Extend `todo_cli` so that `python3 -m todo_cli add <text>` appends a new open
item to `TODOS.md` in the current working directory and exits 0. Multiple words
after `add` are joined with single spaces (`add buy milk` → `buy milk`).

The on-disk format is one item per line: `- [ ] <text>` for open items (and
`- [x] <text>` for done items, which later tasks produce). Adding when
`TODOS.md` does not exist creates it; adding when it already exists appends the
new line and preserves all prior content, byte-for-byte and in order. With no
text after `add`, print a usage line to **stderr** and exit 2 without writing
anything.

## Acceptance criteria
- Running `python3 -m todo_cli add buy milk` in an empty working directory creates `TODOS.md` whose entire contents are exactly `- [ ] buy milk\n`, and exits 0.
- Running `python3 -m todo_cli add` with no further arguments prints a usage line to stderr, writes nothing, and exits 2.
- Adding to a non-empty `TODOS.md` appends the new open item as the last line without modifying or reordering any prior line.
