---
tags:
  - "data"
  - "original"
context:
  - "[[Vim]]"
  - "[[NeoVim]]"
---

# Vim Motions

Vim motions are the commands used to control and navigate [[Vim]] and [[NeoVim]]. They are also used in other software that supports them.

---

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

`f <x>`: Next `<x>` on the line.
`F <x>`: Previous `<x>` on the line.

`t <x>`: Before next `<x>` on the line.
`T <x>`: Before previous `<x>` on the line.

`;`: Next line match.
`,`: Previous line match.

`%`: Matching parentheses or other.

## Normal Mode

_Manipulation mode where input keys are used as actions._

`i`: Insert before.
`a`: Insert after.

`I`: Insert at start of line.
`A`: Insert at end of line.

`o`: New line below.
`O`: New line above.

`d`: Delete (pending).
`D`: Delete until end of line.

`c`: Change (pending).
`C`: Change until end of line.

`y`: Yank (pending).
`Y`: Yank until end of line.

`p`: Paste after.
`P`: Paste before.

`r`: Replace character.
`x`: Delete character.

`v`: Enter visual mode.
`V`: Enter visual line mode.
`Ctrl v`: Enter visual block mode.

`J`: Join bottom line.

`>`: Indent (pending).
`<`: Unindent (pending).

`u`: Undo.
`Ctrl r`: Redo.

`g u`: Lowercase (pending).
`g U`: Upercase (pending).
`Shift ~`: Toggle case under cursor.

`Ctrl a`: Number increment.
`Ctrl x`: Number decrement.

## Search

_Search for patterns in the current file._

`/<pattern>`: Search pattern.

`*`: Search word under cursor.

`n`: Next match.
`N`: Previous match.

## Camera

_Camera movement._

`zz`: Camera to cursor as center.
`zb`: Camera to cursor as bottom.
`zt`: Camera to cursor as top.

`zh`: Move camera left.
`zl`: Move camera right.

## Scroll

_Vertical file scrolling with both camera and cursor._

`Ctrl d`: Scroll down half page.
`Ctrl u`: Scroll up half page.

`Ctrl f`: Scroll down full page.
`Ctrl b`: Scroll up full page.

## Command Mode

_Various commands. Think of it as a small integrated terminal._

**Colon**: Use command mode with the `:` key. Supports tab completions. Press `Enter` to run the command.

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

_Splits are controlled by `Ctrl w` keymaps._

`Ctrl w h`: Focus left split.
`Ctrl w j`: Focus bottom split.
`Ctrl w k`: Focus top split.
`Ctrl w l`: Focus right split.

`Ctrl w w`: Focus next split.

`Ctrl w v`: Open vertical split.
`Ctrl w s`: Open horizontal split.

`Ctrl w q`: Close split.

`Ctrl w x`: Swap splits.

## Pending Mode

_Actions can interact and depend on other actions._

**Pending**: Many actions are insufficient on their own, entering a "Pending" mode, which awaits the next action in the chain.

- Example: Pressing `d` in normal mode alone does not delete anything, but it waits for another action to tell it what to delete. `dd` will delete the whole line. `dfa` will delete from the cursor to the next `a` letter found on the same line.

**Surround**: The keys `a` and `i` have special behavior when used after pending actions. `a` can surround "around", and `i` can surround "inside".

- Example: `di"` will delete everything inside the next quotes. `va(` will select everything inside the next parentheses, including the parentheses themselves.

## Visual Mode

_Visual mode allows for text selection and actions on the selected text._

**Modes**: There are multiple visual modes that select differently:

- **Visual Mode**: Selects characters.
- **Visual Line**: Selects whole lines.
- **Visual Block**: Selects blocks of text.

**Cursor Movement**: The selection follows the movement of the cursor. This works with cursor navigation actions.

- Example: Arrows `h j k l` move the cursor, thus moving the selection. Jumps like `G` will do the same.

**Action Target**: In visual mode, many normal mode actions that would otherwise apply to the cursor apply to the whole selection.

- Example: Using `r` in normal mode will replace the character under the cursor, but in visual mode it will replace all selected characters.

**Pending Actions**: Actions that would otherwise be pending are applied to the selection in visual mode.

- Example: Using `d` in normal mode will await the next action, but in visual mode it will target the selection and delete it.

`u`: Lowercase selection.
`U`: Uppercase selection.

## Insert Mode

_Default writing mode._

`Esc`: Exit insert mode.
`Ctrl c`: Exit insert mode.

**Control Actions**: There are useful actions available while writing in insert mode. They are accessed by the `Ctrl` key.

`Ctrl h`: Delete the character before the cursor.
`Ctrl w`: Delete the word before the cursor.
`Ctrl u`: Delete to line start.

`Ctrl t`: Indent (shift right) the current line.
`Ctrl d`: Dedent (shift left) the current line.

`Ctrl v`: Insert the next character literally.

`Ctrl r <register>`: Paste the contents of a register.

`Ctrl r =`: Evaluate an expression and insert the result.

## Registers

_Reusable storage locations indexed by letters._

`"<register><action>`: Performns an action with a register.

- Example: `"wyy` will copy to the `w` register. `"wp` will paste from the `w` register.

## Repeat

_There are many ways to repeat previous actions._

**Numbers**: Any number `n` before an action generally repeats the action `n` number of times.

- Example: Using `12j` will go down `12` times. Think of it as pressing `j` twelve times.
- There are smart nuances to this. For example spamming `r a` will replace the character under the cursor with `a`, but doing `3 r a` will replace the next `3` characters with `a`.

**Dot**: Actions can be repeated using the `.` dot key.

`.`: Repeat last full action.

**Insert Mode**: In the context of action repeats, everything you do for the duration of a single insert is treated as one command.

- Example: Enter insert mode by opening a new line above with `O`, write some text, exit insert mode with `Ctrl c`. Then, if you press `.` to repeat, it will paste the text you wrote on the line above.

**Macros**: Sequences of key-presses can be stored as a macro under a register to be repeated.

`q<register>`: Start recording macro to register. Use `q` to stop.
`@<register>`: Use macro from register.
`@@`: Shorthand to use last macro again.
