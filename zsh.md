## Random zsh facts

- use `zsh -f` to run it without *rc files!

- zsh has a **Tetris** game, both as a widget or as a curses program:
``` sh
autoload -U tetris
zle -N tetris
bindkey '^k' tetris

autoload -U tetriscurses
tetriscurses
```
- zsh has a built-in Regen batch file editor: it can move, copy or link files based on a pattern
``` sh
zmv '(*)(word.).lis' '$1$2.txt'
zcp [same as zmv -C]
zln [same as zmv -L]
```


## Completion

- Tip: run e.g. `ls *(<tab>` to get help regarding globing.

## Key bindings

- `^z` is to put job into background (suspend)

- Some defaults:
``` sh
# Incremental search for / and ? (standard behaviour)
bindkey -M vicmd "/" history-incremental-search-backward
bindkey -M vicmd "?" history-incremental-search-forward

# allow ctrl-h, ctrl-w, ctrl-? for char and word deletion
# (standard behaviour)
bindkey '^?' backward-delete-char
bindkey '^h' backward-delete-char
bindkey '^w' vi-backward-kill-word
```

- Not binded: `^a`, `^b`, `^k`

# List of keys (as recognized by my terminal):
- [F1]=`^[OP`
- [F2]=`^[OQ`
- [F3]=`^[OR`
- [F4]=`^[OS`
- [F5]=`^[[15~`
- [F6]=`^[[17~`
- [F7]=`^[[18~`
- [F8]=`^[[19~`
- [F9]=`^[[20~`
- [F10]=`^[[21~`
- [F11]=`^[[23~`
- [F12]=`^[[24~`
- [Backspace]=`^?`
- [Insert]=`^[[4h`
- [Home]=`^[[H`
- [PageUp]=`^[[5~`
- [Delete]=`^[[P`
- [End]=`^[[4~`
- [PageDown]=`^[[6~`
- [Up]=`^[[A`
- [Left]=`^[[D`
- [Down]=`^[[B`
- [Right]=`^[[C`
