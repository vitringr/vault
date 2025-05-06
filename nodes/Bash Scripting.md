---
context:
  - "[[Bash]]"
---

#wip

# Bash Scripting

Automating [[Bash]] by executing commands from files.

---

**Command Execution Order**: Commands are run in a sequence from top to bottom.

**Shebang**: Start with the shebang `#!` followed by the path to Bash on the first line.

```bash
#!/bin/bash
echo "Hello, World!"
```

**Comments**: Comments start with a `#` and Bash ignores them.

```bash
# This is a comment.
```

**Semicolons**: Semicolons `;` can be used to run multiple commands on the same line.

```bash
echo "Number one"; echo "Number two"
```

## Variables

**Declare**: Declare variables by assigning a value to a name using the `=` sign without spaces.

**Access**: To access the value of a variable, prefix it with the `$` dollar sign.

```bash
name="World"
echo "Hello, $name!"
```

**Untyped**: Variables in Bash are untyped. They can hold any type of data.
