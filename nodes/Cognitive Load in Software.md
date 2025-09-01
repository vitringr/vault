---
tags:
  - "article"
context:
  - "[[Software Development]]"
---

#wip

# Cognitive Load in Software

Reference: [Cognitive Load](https://github.com/zakirullin/cognitive-load)

Cognitive load in software is how much a developer needs to think in order to complete a task.

---

## Introduction

There are so many buzzwords and best practices out there, but most of them have failed. We need something more fundamental, something that can't be wrong.

Sometimes we feel confusion going through the code. Confusion costs time and money. Confusion is caused by high cognitive load. It's not some fancy abstract concept, but rather a fundamental human constraint. It's not imagined, it's there and we can feel it.

Since we spend far more time reading and understanding code than writing it, we should constantly ask ourselves whether we are embedding excessive cognitive load into our code.

## Cognitive Load

When reading code, you put things like values of variables, control flow logic and call sequences into your head. The average person can hold roughly four such chunks in working memory. Once the cognitive load reaches this threshold, it becomes much harder to understand things.

Let's say we have been asked to make some fixes to a completely unfamiliar project. We were told that a really smart developer had contributed to it. Lots of cool architectures, fancy libraries and trendy technologies were used. In other words, the author had created a high cognitive load for us.

We should reduce the cognitive load in our projects as much as possible.

## Types of Cognitive Load

**Intrinsic**: Caused by the inherent difficulty of a task. It can't be reduced, it's at the very heart of software development.

**Extraneous**: Created by the way the information is presented. Caused by factors not directly relevant to the task, such as smart author's quirks. Can be greatly reduced. We will focus on this type of cognitive load.

## Examples

### Complex Conditionals

```
if  val > someConstant                  // [🧠1]
    && (condition2 || condition3)       // [🧠3] prev cond should be true, one of c2 or c3 has be true
    && (condition4 && !condition5) {    // [🧠4+] we are messed up by this point
    ...
}

```

Introduce intermediate variables with meaningful names:

```
isValid = val > someConstant
isAllowed = condition2 || condition3
isSecure = condition4 && !condition5

// [🧠0] we don't need to remember the conditions, there are descriptive variables

if isValid && isAllowed && isSecure {
    ...
}
```

### Nested ifs

```
if isValid {            // [🧠1] okay nested code applies to valid input only
    if isSecure {       // [🧠2] we do stuff for valid and secure input only
        stuff           // [🧠3]
    }
}
```

Compare it with the early returns:

```
if !isValid
    return

if !isSecure
    return

// [🧠0] we don't really care about earlier returns, if we are here then all good

stuff       // [🧠1]
```

We can focus on the happy path only, thus freeing our working memory from all sorts of preconditions.

### Inheritance Nightmare

We are asked to change a few things for our admin users: `[🧠0]`

```
AdminController extends UserController extends GuestController extends BaseController
```

Ohh, part of the functionality is in `BaseController`, let's have a look: `[🧠1]`
Basic role mechanics got introduced in `GuestController`: `[🧠2]`
Things got partially altered in `UserController`: `[🧠3]`
Finally we are here, `AdminController`, let's code stuff! `[🧠4]`

Oh, wait, there's `SuperuserController` which extends `AdminController`. By modifying `AdminController` we can break things in the inherited class, so let's dive in `SuperuserController` first: `[🧠5+]`

Prefer [[Composition Over Inheritance]].

### Too many small methods, classes or modules

_Method, class and module are interchangeable in this context._

Mantras like "methods should be shorter than 15 lines of code" or "classes should be small" turned out to be somewhat wrong.

**Deep Module**: Simple interface, complex functionality
**Shallow Module**: Interface is relatively complex to the small functionality it provides

Having too many shallow modules can make it difficult to understand the project. Not only do we have to keep in mind each module responsibilities, but also all their interactions. To understand the purpose of a shallow module, we first need to look at the functionality of all the related modules. Jumping between such shallow components is mentally exhausting, linear thinking is more natural to us humans.

Information hiding is paramount, and we don't hide as much complexity in shallow modules.

> The best components are those that provide powerful functionality yet have a simple interface.
> \- John K. Ousterhout

The interface of the UNIX I/O is very simple. It has only five basic calls:

```
open(path, flags, permissions)
read(fd, buffer, count)
write(fd, buffer, count)
lseek(fd, offset, referencePosition)
close(fd)
```

A modern implementation of this interface has hundreds of thousands of lines of code. Lots of complexity is hidden under the hood. Yet it is easy to use due to its simple interface.


