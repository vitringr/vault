---
context:
  - "[[C (Programming Language)]]"
  - "[[Union (Data Type)]]"
---

# C Unions

Union types in the C programming language.

---

Union type variables can hold values of different types (sizes) at different times, but only one type at a time.

```c
union Morph {
  int one;
  float two;
  char three[20];
};

union Morph aer;

aer.one = 42;
aer.two = 13.56;
```

Unions can also be declared using [[C Typedef]]:

```c
typedef union {
  int one;
  float two;
  char three[20];
} Morph;

Morph aer;

aer.one = 42;
aer.two = 13.56;
```
