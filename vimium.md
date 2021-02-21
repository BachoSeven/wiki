### Visual mode
- `o` swaps anchor and focus of the visual selection
### Filtered hints
- `<c-Space>` rotates the stacking order (configured)
### Move this tab to end/beginning
``` js
map <a-,> moveTabLeft count=99
map <a-.> moveTabRight count=99
```
## Find mode
### Regex
- append `\r` to the search query to force treating expression as a JS regex.

## Tab navigation
- `^` is like a single `<C-Tab>` in Firefox

## Page navigation
- `gi` goes to the first input field
- `ge` edits the current url and go to it
- `gE` edit current url and open in new tab
