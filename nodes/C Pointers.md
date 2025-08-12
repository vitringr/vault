---
context:
  - "[[C (Programming Language)]]"
  - "[[Pointer]]"
---

# C Pointers

Pointers in the C programming language.

---

Variable that stores the memory address of another variable.

Pointers must point to specific [[C Data Types]].

## Address

(Referencing)

The unary operator `&` gives the address of its target.

```c
int var = 42;
printf("%p", &var); // 0x7ffdc3229904
```

The address of the target can be assigned to a pointer.

```c
int var = 42;
int *p = &var; // *p points to var
```

## Indirection

(Dereferencing)

The unary operator `*` applied to a pointer can access its target.

```c
int var = 42;
int *p = &var;
printf("%d", *p); // 42
```

## Pointer Arithmetic

Pointers support arithmetic operations on their addresses.

**Type-aware**: The base unit (1) of pointer arithmetic is the size of the pointed-to data type.

```c
int arr[5];

int *p = arr; // points to arr[0]
p += 2; // jumps 8 bytes forward (2 * sizeof(int))
```

Operations such as `++` or `--` increment/decrement by one _element_ (not by one byte!).

## Array Operations

The value of a variable of type array is the address of element zero of the array.

Since the name of the array is a synonym for the location of the initial element, these assignments are equal:

```c
int *p = &arr[0];
int *p = arr;
```

The forms `array[index]` and `dereference(arrayName + index)` are also identical:

```c
int *p = arr;

arr[3];
*(p + 3);
```

Function parameters are also equivalent:

```c
void hehe(int *arr) { ... }
void hehe(int arr[]) { ... }
```

**Difference**: The difference between the array name and a pointer to the array is that the pointer is a variable, but the array name is not. Thus there are some address arithmetic operations that can be done on the pointer (like `p++`), but not on the array name.

## Pointer to Pointer

Pointers can copy the address of other pointers, thus pointing to their target.

Since pointers are variables, they can be used without dereferencing.

```c
int var = 42;

int *pA = &var;

int *pB;
pB = pA;

printf("%d", *pB); // 42
```

## Zero

Zero is the only integer that is interchangeable between pointers and integers.

C guarantees that `0` is never a valid address for data.

Pointers can be initialized to zero `0`. The symbolic constant `NULL` is often used in place of zero for clarity.

```c
int *anyP = 0;
int *anyP = NULL;
```
