---
context:
  - "[[C (Programming Language)]]"
---

# C Literals

Literals in the C programming language.

---

Hard-coded values in the program:

```c
42;
3.14159f;
'A';
"B";
```

## Character Literals

Enclosed in single quotes (`'A'`).

```c
char letter = 'A';     // Simple character
char newline = '\n';   // Escape sequence
char null_char = '\0'; // Null terminator
```

### Escape sequences:

| Escape sequence | Character represented                                                                |
| --------------- | ------------------------------------------------------------------------------------ |
| `\a`            | Alert (Beep, Bell)                                                                   |
| `\b`            | Backspace                                                                            |
| `\f`            | Formfeed Page Break                                                                  |
| `\n`            | Newline (Line Feed); see below                                                       |
| `\r`            | Carriage Return                                                                      |
| `\t`            | Horizontal Tab                                                                       |
| `\v`            | Vertical Tab                                                                         |
| `\\             | Backslash                                                                            |
| `\'`            | Apostrophe or single quotation mark                                                  |
| `\"`            | Double quotation mark                                                                |
| `\?`            | Question mark (used to avoid trigraphs)                                              |
| `\nnn`          | The byte whose numerical value is given by `nnn` interpreted as an octal number      |
| `\xhh`...       | The byte whose numerical value is given by `hh`… interpreted as a hexadecimal number |
| `\uhhhh`        | Unicode code point below `10000` hexadecimal (C23)                                   |
| `\Uhhhhhhhh`    | Unicode code point where `h` is a hexadecimal digit (C23)                            |

## String Literals

Enclosed in double quotes (`"Hello"`).

Stored as null-terminated `char` arrays (`'H','e','l','l','o','\0'`).

**Immutable**: Modifying them leads to undefined behavior.

```c
char str[] = "Hello";          // Modifiable copy
const char *ptr = "World";     // Read-only (best practice)
printf("%s", "C Programming"); // Direct usage
```

**Quotes**: Note that `'A'` is a single character (1 byte) `A`, while `"A"` is a string (2 bytes) `A` + `\0`.
