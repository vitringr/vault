---
context:
  - "[[C (Programming Language)]]"
---

# C Preprocessor

Text substitution that runs before [[Compilation]].

---

Processes directives (commands starting with `#`) to transform the [[Source Code]] before the [[Compiler]] uses it.

## File Inclusion

`#include`

```c
#include <stdio.h>      // System header
#include "myheader.h"   // User header
```

Copies entire content of the file into current source.

The `<>` searches system paths, while `""` searches local directory first.

## Macro Definition

See [[C Macros]]

`#define`

```c
#define PI 3.14159
```

Simple text replacement before compilation.

**Removal**: Use `#undef` to remove macro definitions.

```c
#undef PI
```

## Conditional Compilation

```c
#ifdef DEBUG
    printf("Debug mode\n");
#endif

#if VERSION > 2
    // Code for version 3+
#elif VERSION == 2
    // Code for version 2
#else
    // Default code
#endif
```


