---
context:
  - "[[Neovim]]"
  - "[[Godot]]"
---

# Integrating Neovim to Godot

Trying to make [[Neovim]] work as the code editor of [[Godot]].

---

Running an LSP without any advanced configuration.

In Godot, open `Editor ⇒ Editor Settings ⇒ Text Editor ⇒ External` and in there set the _Use External Editor_ to true, and set the _Exec Path_ to `/usr/bin/nvim`.

Actually, I'm not sure if I need the exec path thing.

In Neovim, work from the directory where the Godot project is, and do `:LspStart gdscript` at the beginning.
