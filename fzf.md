## Preview window
- The preview window uses `$SHELL -c` to execute commands.

## Chromium bookmarks Ruby(/Bash) script
``` ruby
#!/bin/zsh

# bm - browse Chrome bookmarks with fzf
# vim: ft=zsh
# Credits:
    # Original version by junegunn: https://gist.github.com/junegunn/15859538658e449b886f
    # Zsh version merged from fzf's wiki: https://github.com/junegunn/fzf/wiki/Browse-chrome-bookmarks

# Make sure $BROWSER is set; I could have used xdg-open,
# but for use as a popup it is more convenient this way.
# For usage as a popup: `bm popup`
# NOTE: You might want to install w3m for the preview window in fzf.

local ruby output
  ruby=$(which ruby)
  output=$($ruby << EORUBY
# encoding: utf-8

require 'json'
FILE = '/home/fra/.config/chromium/Default/Bookmarks'
CJK  = /\p{Han}|\p{Katakana}|\p{Hiragana}|\p{Hangul}/

def build parent, json
  name = [parent, json['name']].compact.join('/')
  if json['type'] == 'folder'
    json['children'].map { |child| build name, child }
  else
    { name: name, url: json['url'] }
  end
end

def just str, width
  str.ljust(width - str.scan(CJK).length)
end

def trim str, width
  len = 0
  str.each_char.each_with_index do |char, idx|
    len += char =~ CJK ? 2 : 1
    return str[0, idx] if len > width
  end
  str
end

width = `tput cols`.to_i / 2
json  = JSON.load File.read File.expand_path FILE
items = json['roots']
        .values_at(*%w(bookmark_bar synced other))
        .compact
        .map { |e| build nil, e }
        .flatten

items.each do |item|
  name = trim item[:name], width
  puts [just(name, width),
        item[:url]].join("\t\x1b[36m") + "\x1b[m"
end
EORUBY
)
	[[ $1 = popup ]] && opts="--height=100%"
	echo -e "$output"						|
	fzf --ansi --multi --no-hscroll --tiebreak=begin		\
	--preview "echo {-1} | xargs readable -q | w3m -T text/html"	\
	--preview-window=right:30% $opts				|
	awk 'BEGIN { FS = "\t" } { print $2 }'				|
	setsid -f xargs -r $BROWSER >/dev/null
```
