# Capitalization
- `u`/`U` for visual mode
- `gu`/`gU`<motion> for normal mode
- `~` switches capitalization, `g~`<motion> does the same on a motion.

# Registers
- `"=` is the *expression* register, it eats vimscript expressions

# Marks
- `mx` sets a mark at cursor, per buffer
- `mX` sets a mark at cursor, **globally**
- `'x` (resp. `'X`) jumps to the `x`/`X` mark

# Visual mode
- `o` moves to the "other end" of the selection
  (for rectangular blocks, it's the opposite corner)

# Formatting
- `gq`<motion> formats the selected lines, using `textwidth`

# History

- `q/` opens an interactive search history
- `:<C-f>` opens an interactive command-line history; also through `q:`, but we reserved that for the fzf version of cli history.

# `z-*` stuff

- Spelling: `zg` good, `zw` bad; `zug` and `zuw` undo.
- `zt`, `zb`, `zz` to move view maintaining cursor;
- Folds, tl;dr: `za` to toggle fold(`zA` recursively), `zc` to close it(`zC` recursively), `zO` to open folds recursively(`zo`), `zd` to delete a fold(`zD` recursively), `zf` to create folds with movements, `zE` to eliminate folds entirely; `z[j-k]` are for navigating around folds.
- To save folds on exit: `:mkview`

# Random stuff

- `earlier` command
- `ge` and `gE` are `e` and `E` but going backwards
- `gv` *goes to the last selection*
- `gq` is the basic comand to *format* lines
- `:scriptnames` lists the loaded scripts (i.e. plugins)
- `:verbose COMMAND is useful to debug stuff`
- `set list` shows unprintable characters

# Fold-Markers
- Using `foldmethod=marker`, one can write `{{{1` in a comment to open a fold (no need to close it, but you can with `}}}1`)

# AutoCommands
## Temporarily disable aucmds
`:au!`

# Vimtex
- `ctrl-x_ctrl-O` starts omni completion (amazing)

# Tags
## Creation
- install `ctags`
- `!ctags -R .` (i.e. prepend `command! MakeTags` and map it)
## Keybindings
- ^] jump to tag under cursor
- g^] for ambiguous tags
- ^t jumps back up the tag stack

# Built-in Autocompletion
- ^x^n for JUST this file
- ^x^f for filenames
- ^x^] for TAGS
- ^n for anything

# Modelines
- See `:help modelines`. (things like `vim:set et sw=4 ts=4 tw=180:`)

# Replace tabs with spaces:
``` sh
1,$s/\t/ /g
```
