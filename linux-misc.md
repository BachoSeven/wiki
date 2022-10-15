## Resolving relative paths and symlinks
- If you need the absolute path of anything, including following symlinks to their actual file path, use
  `readlink -f` or `realpath`.
- If you just need the absolute path AND don't want to follow symlinks, use
  `realpath -s`

## Finding which processes are accessing certain files
- `fuser -fv FILE`

## /etc/issue file escape codes
``` sh
- \b : Insert the baudrate of the current line.
- \d : Insert the current date.
- \s : Insert the system name, the name of the operating system.
- \l : Insert the name of the current tty line.
- \m : Insert the architecture identifier of the machine, eg. i486
- \n : Insert the nodename of the machine, also known as the hostname.
- \o : Insert the domainname of the machine.
- \r : Insert the release number of the OS, eg. 1.1.9.
- \t : Insert the current time.
- \u : Insert the number of current users logged in.
- \U : Insert the string “1 user” or “ users” where is the number of current users logged in.
- \v : Insert the version of the OS, eg. the build-date etc.
```

## Virtual Console
# Scrollback

- `Shift`+[`PgUp`,`PgDown`]

## X Server
- `xset q` gives you lots of nice information about your current session's configuration.

## Nice Figlet Fonts
- colossal
- future (!)
- speed
- computer
- emboss
- emboss2
- Merlin1
- ghost
- Merlin2
- coinstack
- larry3d
- chunky
- lean
- miniwi
- rebel
- alpha
- calvin s
- twisted
- univers

## Randomly nice packages
- `fzwal-git`
- `mgba`
- `snake-ncurses`
- `vixl44-git`: pixel art :]
### disk usage apps
- `ncdu`
- `duf`
- `vizex`

## Mount .iso dvd image
- `sudo mount -t iso9660 -o ro,loop .iso /mnt/iso`

## Grub
### Interesting "ricing" kernel command-line options
``` ini
        vt.color=       [VT] Default text color.
                        Format: 0xYX, X = foreground, Y = background.
                        Default: 0x07 = light gray on black.


        vt.default_blu= [VT]
                        Format: <blue0>,<blue1>,<blue2>,...,<blue15>
                        Change the default blue palette of the console.
                        This is a 16-member array composed of values
                        ranging from 0-255.

        vt.default_grn= [VT]
                        Format: <green0>,<green1>,<green2>,...,<green15>
                        Change the default green palette of the console.
                        This is a 16-member array composed of values
                        ranging from 0-255.

        vt.default_red= [VT]
                        Format: <red0>,<red1>,<red2>,...,<red15>
                        Change the default red palette of the console.
                        This is a 16-member array composed of values
                        ranging from 0-255.

        vt.default_utf8=
                        [VT]
                        Format=<0|1>
                        Set system-wide default UTF-8 mode for all tty's.
                        Default is 1, i.e. UTF-8 mode is enabled for all
                        newly opened
        vt.cur_default= [VT] Default cursor shape.
                       Format: 0xCCBBAA, where AA, BB, and CC are the same as
                       the parameters of the <Esc>[?A;B;Cc escape sequence;
                       see VGA-softcursor.txt. Default: 2 = underline.

        vt.default_blu= [VT]
                        Format: <blue0>,<blue1>,<blue2>,...,<blue15>
                        Change the default blue palette of the console.
                        This is a 16-member array composed of values
                        ranging from 0-255.

        vt.default_grn= [VT]
                        Format: <green0>,<green1>,<green2>,...,<green15>
                        Change the default green palette of the console.
                        This is a 16-member array composed of values
                        ranging from 0-255.

        vt.default_red= [VT]
                        Format: <red0>,<red1>,<red2>,...,<red15>
                        Change the default red palette of the console.
                        This is a 16-member array composed of values
                        ranging from 0-255.

        vt.default_utf8=
                        [VT]
                        Format=<0|1>
                        Set system-wide default UTF-8 mode for all tty's.
                        Default is 1, i.e. UTF-8 mode is enabled for all
                        newly opened terminals.

        vt.global_cursor_default=
                        [VT]
                        Format=<-1|0|1>
                        Set system-wide default for whether a cursor
                        is shown on new VTs. Default is -1,
                        i.e. cursors will be created by default unless
                        overridden by individual drivers. 0 will hide
                        cursors, 1 will display them.

        vt.italic=      [VT] Default color for italic text; 0-15.
                        Default: 2 = green.

        vt.underline=   [VT] Default color for underlined text; 0-15.
                        Default: 3 = cyan.
```

## Securely removing files
```
shred --remove FILE
```

## Useful commands for memory and cpu usage
- used memory: ` free -h|awk '/^Mem:/ {print $3 "/" $2}'`
- cpu consuming processes: `ps axch -o cmd:18,%mem,pid --sort -%mem|head`
- top configuration: `zxcVm1t0W`
