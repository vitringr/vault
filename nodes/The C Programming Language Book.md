---
tags:
  - book
context:
  - "[[C (Programming Language)]]"
---

# The C Programming Language Book

Any notes from the book.

Book: `The C Programming Language (Second Edition)`

---

## Introduction

C is a general purpose programming language.

The language is not tied to any operating system or machine.

**Data Types**: C provides a variety of data types. The fundamental types are characters, and integers and floating-point numbers of several sizes. In addition, there is a hierarchy of derived data types created pointers, arrays, structures, and unions.

**Expressions**: Expressions are formed from operators and operands. Any expression can be a statement.

**Pointers**: Pointers provide for machine-independent address arithmetic.

**Control Flow**: C provides the fundamental control-flow constructions required for well-structured programs: statement grouping, decision making, selecting one of a set of possible cases, looping with the termination test at the top or bottom, and early loop exit.

**Functions**: Functions may return valeus of basic types, structures, unions, or pointers. Any function may be called recursively. Local variables are typically "automatic", or created anew with each invocation. Function definitions may not be nested but variables may be declared in a block-structured fashion. The functions of a C program may exist in separate source files that are compiled separately. Variables may be internal to a function, external but known only within a single source file, or visible to the entire program.

**Preprocessing**: A preprocessing step performs macro substitution on program text, inclusion of other source files, and conditional compilation.

**Low-level**: C is relatively low level, meaning that it deals with the same sort of objects that most computers do - characters, numbers, and addresses. These may be combined and moved about with the arithmetic and logical operators implemented by real machines.

**Barebone**: C provides no operations to deal directly with composite objects such as character strings, sets, lists, or arrays. There are no operations that manipulate an entire array or string, although structures may be copied as a unit. The language does not define any storage allocation facility other than static definition and the stack discipline provided by the local variables or functions; there is no heap or garbage collection. Finally, C itself provides no input/output facilities; there are no READ or WRITE statements, and no built-in file access methods. All of these higher-level mechanisms must be provided by explicitly called functions. Most C implementations have included a reasonably standard collection of such functions.

**Straightforward**: C offers only straightforward, single-thread control flow: tests, loops, grouping, and subprograms, but not multiprogramming, parallel operations, synchronization, or coroutines.

**Minimalism**: The minimalistic design of C is one of the things that makes it so good. A programmer can reasonably expect to know and understand and indeed regularly use the entire language.

**Portable**: It is easy to write portable programs, as C is independent of any particular machine architecture. The programs can be run without change on a variety of different hardware.

---

#wip
