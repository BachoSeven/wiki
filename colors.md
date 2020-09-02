# Text attributes
-  0  All attributes off
-  1  Bold on
-  4  Underscore (on monochrome display adapter only)
-  5  Blink on
-  7  Reverse video on
-  8  Concealed on


# Foreground colors
-  0;30   Black          1;30   Dark Gray
-  0;34   Blue           1;34   Light Blue
-  0;32   Green          1;32   Light Green
-  0;36   Cyan           1;36   Light Cyan
-  0;31   Red            1;31   Light Red
-  0;35   Purple         1;35   Light Purple
-  0;33   Brown          1;33   Yellow
-  0;37   Light Gray     1;37   White


# Background colors
-  40   Black
-  41   Red
-  42   Green
-  43   Yellow
-  44   Blue
-  45   Magenta
-  46   Cyan
-  47   White

## Examples
### Escape sequence
``` sh
\033[<code>m or \e[<code>m

color : \[\033[ <code>m\] \]

e.g.
bg=Blue, Bold, fg=Red
1. \033[44;1;31m
2. \033[44m\033[1;31m
```

### Sources
-  http://ascii-table.com/ansi-escape-sequences.php
-  http://archive.linux.or.jp/JF/JFdocs/Bash-Prompt-HOWTO-5.html
