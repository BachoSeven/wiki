## Globbing
#### Symbols
``` sh
/      directories
.      plain files
@      symbolic links
=      sockets
p      named pipes (FIFOs)
*      executable plain files (0100)
%      device files (character or block special)
%b     block special files
%c     character special files
r      owner-readable files (0400)
w      owner-writable files (0200)
x      owner-executable files (0100)
A      group-readable files (0040)
I      group-writable files (0020)
E      group-executable files (0010)
R      world-readable files (0004)
W      world-writable files (0002)
X      world-executable files (0001)
s      setuid files (04000)
S      setgid files (02000)
t      files with the sticky bit (01000)
```
#### Advanced examples
``` sh
print *(m-1)          # Modification time: up to a day ago
print *(a1)           # Access time: accessed a day ago
print *(@)            # Symbolic links
print *(Lk+50)        # Files larger than 50 kilobytes
print *(Lk-50)        # Files smaller than 50 kilobytes
print **/*.c          # All *.c files under $PWD
print **/*.c~file.c   # All *.c files which are not 'file.c'
print (foo|bar).*     # All files beginning with 'foo' or 'bar'
print *~*.*           # Only files whose name does not contain '.'
chmod 644 *(.^x)      # Make all non-executable files publically readable
print -l *(.c|.h)     # All files ending in '.c' or '.h'
print **/*(g:users:)  # All files/directories belonging to the users group
echo /proc/*/cwd(:h:t:s/self//) # Analogous to `ps ax | awk '{print $1}'`
echo (../)#foo        # All 'foo' files in the current or parent directories
noglob zmv -W ??\ * 0??\ *  # move 01 to 001, 02 to 002, etc
```

## Colors
```
This  function  initializes several associative arrays to map color names to (and from) the ANSI stan‐
dard eight-color terminal codes.  These are used by the prompt theme system (see above).   You  seldom
should need to run colors more than once.

The  eight  base colors are: black, red, green, yellow, blue, magenta, cyan, and white.  Each of these
has codes for foreground and background.  In addition there  are  seven  intensity  attributes:  bold,
faint,  standout,  underline,  blink,  reverse,  and  conceal.  Finally, there are seven codes used to
negate attributes: none (reset all attributes to the  defaults),  normal  (neither  bold  nor  faint),
no-standout, no-underline, no-blink, no-reverse, and no-conceal.
```
## Random zsh facts

- use `zsh -f` to run it without sourcing any configuration!
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


# Completion

- Tip: run e.g. `ls *(<tab>` to get help regarding globing.

# Key bindings

- `^z` is to put job into background (suspend)

- Some defaults:
``` sh
# allow ctrl-h, ctrl-w, ctrl-? for char and word deletion
# (standard behaviour)
bindkey '^?' backward-delete-char
bindkey '^h' backward-delete-char
bindkey '^w' vi-backward-kill-word
```

### Vi-mode
#### History search from `cmd` mode
```
"/" vi-history-search-backward
"?" vi-history-search-forward
"n" vi-repeat-search
"N" vi-rev-repeat-search
```

- Not binded: `^a`, `^b`, `^k`

### HISTORY
#### History bangs
```
!42      # re-run command 42
!!       # re-run last command
!v       # re-run last command that started with 'v'
!?foo?   # re-run last command that had the string "foo" anywhere in it
!^       # first argument  of last command
!$       # last  argument  of last command
!!*      # all   arguments of last command
```
#### History complete words
`Alt+/` (amazing)

### List of keys (as recognized by my terminal):
#### HINT: type `read` and hit keys :)
```
[F1]        = ^[OP
[F2]        = ^[OQ
[F3]        = ^[OR
[F4]        = ^[OS
[F5]        = ^[[15~
[F6]        = ^[[17~
[F7]        = ^[[18~
[F8]        = ^[[19~
[F9]        = ^[[20~
[F10]       = ^[[21~
[F11]       = ^[[23~
[F12]       = ^[[24~
[Backspace] = ^?
[Insert]    = ^[[4h
[Home]      = ^[[H
[PageUp]    = ^[[5~
[Delete]    = ^[[P
[End]       = ^[[4~
[PageDown]   = ^[[6~
[Up]        = ^[[A
[Left]      = ^[[D
[Down]      = ^[[B
[Right]     = ^[[C
```
