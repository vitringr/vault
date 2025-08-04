---
tags:
  - "data"
context:
  - "[[C (Programming Language)]]"
  - "[[Data Type (Computer Science)]]"
---

# C Data Types

Data Types in the C programming language.

---

| Type                                                                     | Size (bits) | Format Specifier                                | Range                    | Suffix for Decimal Constants |
| ------------------------------------------------------------------------ | ----------- | ----------------------------------------------- | ------------------------ | ---------------------------- |
| `bool`                                                                   | `1 (8)`     | `%d`                                            | `[false, true]`          | —                            |
| `char`                                                                   | `≥ 8`       | `%c`                                            | `[CHAR_MIN, CHAR_MAX]`   | —                            |
| `signed char`                                                            | `≥ 8`       | `%c`                                            | `[SCHAR_MIN, SCHAR_MAX]` | —                            |
| `unsigned char`                                                          | `≥ 8`       | `%c`                                            | `[0, UCHAR_MAX]`         | —                            |
| `short`, `short int`, `signed short`,`signed short int`                  | `≥ 16`      | `%hi` or `%hd`                                  | `[SHRT_MIN, SHRT_MAX]`   | —                            |
| `unsigned short`, `unsigned short int`                                   | `≥ 16`      | `%hu`                                           | `[0, USHRT_MAX]`         | —                            |
| `int`, `signed`, `signed int`                                            | `≥ 16`      | `%i` or `%d`                                    | `[INT_MIN, INT_MAX]`     | none                         |
| `unsigned`, `unsigned int`                                               | `≥ 16`      | `%u`                                            | `[0, UINT_MAX]`          | `u` or `U`                   |
| `long`, `long int`, `signed long`, `signed long int`                     | `≥ 32`      | `%li` or `%ld`                                  | `[LONG_MIN, LONG_MAX]`   | `l` or `L`                   |
| `unsigned long`, `unsigned long int`                                     | `≥ 32`      | `%lu`                                           | `[0, ULONG_MAX]`         | `u`/`U` and `l`/`L`          |
| `long long`, `long long int`, `signed long long`, `signed long long int` | `≥ 64`      | `%lli` or `%lld`                                | `[LLONG_MIN, LLONG_MAX]` | `ll` or `LL`                 |
| `unsigned long long`, `unsigned long long int`                           | `≥ 64`      | `%llu`                                          | `[0, ULLONG_MAX]`        | `u`/`U` and `ll`/`LL`        |
| `float`                                                                  | `32`        | `%f` `%F` `%g` `%G` `%e` `%E` `%a` `%A`         | Platform-dependent       | `f` or `F`                   |
| `double`                                                                 | `64`        | `%lf` `%lF` `%lg` `%lG` `%le` `%lE` `%la` `%lA` | Platform-dependent       | none                         |
| `long double`                                                            | `80/128`    | `%Lf` `%LF` `%Lg` `%LG` `%Le` `%LE` `%La` `%LA` | Platform-dependent       | `l` or `L`                   |

> [!NOTE]
> **Booleans**: C23's `bool` requires `#include <stdbool.h>`
> **Minimum Sizes**: Sizes are per C standard. Actual sizes may be larger.
> **Format Specifiers**: Format specifiers may vary slightly across compilers.

### Base Prefix

| Prefix | Base         | Example         |
| ------ | ------------ | --------------- |
| `0`    | Octal        | `0123` (`83`)   |
| `0x`   | Hexadecimal  | `0xFF` (`255`)  |
| `0b`   | Binary (C23) | `0b1010` (`10`) |

> [!NOTE]
> **Case-insensitive**: `0xff` is the same as `0xFF`.
> **Binary**: Binary optional in C23, not standard before.

**Combined Suffixes**: Suffixes can be combined and their order does not matter.
