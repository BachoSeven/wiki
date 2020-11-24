# Histories

- `q/` opens an interactive search history
- `:<C-f>` opens an interactive command-line history; also through `q:`, but we reserved that for the fzf version of cli history.

# `z-*` stuff

- Spelling: `zg` good, `zw` bad; `zug` and `zuw` undo.
- `zt`, `zb`, `zz` to move view maintaining cursor;
- Folds, tl;dr: `za` to toggle fold(`zA` recursively), `zc` to close it(`zC` recursively), `zO` to open folds recursively(`zo`), `zd` to delete a fold(`zD` recursively), `zf` to create folds with movements, `zE` to eliminate folds entirely; `z[j-k]` are for navigating around folds.

# Random stuff

- `earlier` command
- `ge` and `gE` are `e` and `E` but going backwards
- `:scriptnames` lists the loaded scripts (i.e. plugins)
- `:verbose COMMAND is useful to debug stuff`
- `set list` shows unprintable characters

# Fold-Markers
- Using `foldmethod=marker`, one can write `{{{1` in a comment to open a fold (no need to close it, but you can with `}}}1`)
