---
context:
  - "[[C (Programming Language)]]"
---

# C Command-Line Arguments

Command-line arguments in C allow input to be passed to the program.

---

The inputs are handled using the `main()` function's parameters when it begins.

When `main()` is called, it is called with two arguments:

- **`argc`**: The number of command-line arguments the program was invoked with.
- **`argv`**: Pointer to an array of character strings that contain the arguments, one per string.

The default `argc` count is at least `1` - where `argv[0]` is the program name.

Arguments are always strings. Manually to numbers if needed.

## Printing Arguments

Simple program to print the arguments and their count:

```c
int main(int argc, char *argv[]) {
  printf("argc: %d\n", argc);

  for (int i = 1; i < argc; i++)
    printf("argv: %s\n", argv[i]);
}
```

The program can also be written like:

```c
int main(int argc, char *argv[]) {
  printf("argc: %d\n", argc);

  while (--argc)
    printf("%s\n", *(++argv));
}
```

## Best Practices

Always check `argc` to avoid crashes:

```c
if (argc <= 1)
  return 1;
```
