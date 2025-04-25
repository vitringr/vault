---
tags:
  - "data"
context:
  - "[[Vim]]"
---

#wip

# Vim Motions

`Esc`: Exit

---

## Command Mode

`:q`: Quit.
`:qa`: Quit all.

`:q!`: Force quit.
`:qa!`: Force quit all.

`:w`: Write.
`:wa`: Write all.

`:bn`: Next buffer.
`:bp`: Previous buffer.
`:bd`: Close buffer.

## Normal Mode

`.`: Repeat last command.

`i`: Insert before.
`a`: Insert after.

`I`: Insert at start of line.
`A`: Insert at end of line.

`o`: New line below.
`O`: New line above.

`d`: Delete.
`D`: Delete until end of line.
`dd`: Delete line.

`c`: Change.
`C`: Change until end of line.
`cc`: Change line.

`y`: Yank.
`Y`: Yank until end of line.
`yy`: Yank line.

`p`: Paste after.
`P`: Paste before.

`/<pattern>`: Search pattern.

`*`: Search word under cursor.

`n`: Next match.
`N`: Previous match.



## Insert Mode

`Esc`: Exit insert mode.
`Ctrl c`: Exit insert mode.

`Ctrl h`: Delete the character before the cursor.
`Ctrl w`: Delete the word before the cursor.
`Ctrl u`: Delete to line start.

`Ctrl t`: Indent (shift right) the current line.
`Ctrl d`: Dedent (shift left) the current line.

`Ctrl v`: Insert the next character literally.

`Ctrl r <register>`: Paste the contents of a register.
`Ctrl r =`: Evaluate an expression and insert the result.
`Ctrl r :`: Insert the last command-mode command.
