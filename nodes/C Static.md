---
context:
  - "[[C (Programming Language)]]"
---

# C Static

Keyword for controlling persistance and encapsulation.

---

The `static` flag means "keep alive" when applied to locals, and "don't export" when applied to globals and functions.

## Local Variables

When applied to local variables in functions, the `static` keyword makes the variable persistent across invocations.

```c
void increase() {
  int a = 0;
  static int sa = 0;

  a++;
  sa++;

  printf("a: %d\tsa: %d\n", a, sa);
}

int main() {
  for (int i = 0; i < 9; i++)
    increase();
}

// Output:
// a: 1    sa: 1
// a: 1    sa: 2
// a: 1    sa: 3
// a: 1    sa: 4
// a: 1    sa: 5
// a: 1    sa: 6
// a: 1    sa: 7
// a: 1    sa: 8
// a: 1    sa: 9
```

The practical difference between a static local variable and a global scope one outside of the function is that the static variable remains encapsulated inside of the function.

The static variable is initialized once, only on the first call.

## Global Variables or Functions

When applied to global variables or functions, the `static` keyword acts as private access control.

Such variables and functions are unaccessible outside of the file.

Like a `private` flag in other languages.
