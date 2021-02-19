# Vim cheatsheet

## Navigation

### Word motion

- w: to move forward to the start of next word
- b: to move backwards to the start of next word
- e: to move forward to the end of next word

### Line and Paragraph motions

- 0: to move to the start of the current line
- ^: to move to the start of the first word of the current line
- $: to move to the end of the current line
- \<C-U\> / \<C-D\>: Page up/page down
- \<Ctrl-G\>: Go to bottom of the file

### Character

- f c: go forward to char c
- F c: go backward to char c

### Go to definition

- \<Ctrl-]\>: go to definition

## Editing

- a: append
- A: append at the end of current line
- i: insert
- I: insert at the start of current line
- o: next line
- O: previous line
- r: replace one char
- u: undo changes
- <Command + { / } >: indentation

## Clipboard

- x: delete character
- dd: delete line (cut)
- yy: yank line (copy)
- p: paste
- P: paste before

## Visual mode

- v: enter visual mode
- V: enter visual line mode

## Folds

- za: Toggle
