---
tags:
  - "data"
  - "original"
context:
  - "[[Vim]]"
  - "[[NeoVim]]"
---

# Vim Motions

Vim motions are the commands used to control and navigate [[Vim]] and [[NeoVim]]. They are also used in other software that supports it.

This is a cheatsheet covering essential commands.

---

## Interactions

_Most commands have shared behavior and interact with other commands._

**Pending**: Many commands enter their own "Pending" mode, which awaits the next command.

- Example: pressing `d` in normal mode alone does not delete anything, it waits for another command to tell it what to delete. `dd` will delete the whole line. `dfa` will delete from the cursor to the next `a` letter found on the same line.

**Visual Mode**: In visual mode, many normal mode commands that would otherwise apply to the cursor apply to the whole selection.

- Example: Using `r` in normal mode will replace the character under the cursor, but in visual mode it will replace all selected characters.

**Numbers**: Any `n` before a command generally repeats the command `n` times.

- Example: Using `12j` will go down `12` times.

`.`: Repeat last command.

`q<register>`: Start recording macro to register. Use `q` to stop.
`@<register>`: Use macro from register.
`@@`: Use last macro again.

## Movement

_Cursor movement and navigation._

`h`: Left.
`j`: Down.
`k`: Up.
`l`: Right.

`w`: Start of next word.
`W`: Same, ignores punctuation.

`b`: Start of previous word.
`B`: Same, ignores punctuation.

`e`: End of current word.
`E`: Same, ignores punctuation.

`H`: Screen beginning.
`L`: Screen ending.

`0`: Line beginning.
`$`: Line ending.

`gg`: First line in file.
`G`: Last line in file.
`<number>g`: To `n` line in file.

## Camera

`zz`: Camera to cursor as center.
`zb`: Camera to cursor as bottom.
`zt`: Camera to cursor as top.

`zh`: Move camera left.
`zl`: Move camera right.

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
`:ls`: List buffers.
`:b<number>`: Switch to `n` buffer.

`:tabn`: Next tab.
`:tabp`: Previous tab.
`:tabnew`: New tab.

## Splits

_Splits are generally controlled by `Ctrl w` keymaps._

`Ctrl w h`: Focus left split.
`Ctrl w j`: Focus bottom split.
`Ctrl w k`: Focus top split.
`Ctrl w l`: Focus right split.

`Ctrl w w`: Focus next split.

`Ctrl w v`: Open vertical split.
`Ctrl w s`: Open horizontal split.

`Ctrl w q`: Close split.

`Ctrl w x`: Swap splits.

## Normal Mode

`i`: Insert before. **INSERT**
`a`: Insert after. **INSERT**

`I`: Insert at start of line. **INSERT**
`A`: Insert at end of line. **INSERT**

`o`: New line below. **INSERT**
`O`: New line above. **INSERT**

`d`: Delete.
`D`: Delete until end of line.
`dd`: Delete line.

`c`: Change. **INSERT**
`C`: Change until end of line. **INSERT**
`cc`: Change line. **INSERT**

`y`: Yank.
`Y`: Yank until end of line.
`yy`: Yank line.

`p`: Paste after.
`P`: Paste before.

`r`: Replace character.
`x`: Delete character.

`/<pattern>`: Search pattern. **SEARCH**

`*`: Search word under cursor.

`n`: Next match.
`N`: Previous match.

`J`: Join bottom line.

`v`: Select by cursor. **VISUAL**
`V`: Select by line. **VISUAL**
`Ctrl v`: Select by block. **VISUAL**

`>`: Indent.
`<`: Unindent.

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
