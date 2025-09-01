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

P.S. If you think we are rooting for bloated God objects with too many responsibilities, you got it wrong.

### Responsible for One Thing

All too often, we end up creating lots of shallow modules, following some vague "a module should be responsible for one, and only one, thing" principle. What is this blurry one thing? Instantiating an object is one thing, right? So MetricsProviderFactoryFactory seems to be just fine. The names and interfaces of such classes tend to be more mentally taxing than their entire implementations, what kind of abstraction is that? Something went wrong.

We make changes to our systems to satisfy our users. We are responsible to them.

> A module should be responsible to one, and only one user.

This is what this [[Single Responsibility Principle]] is all about. Simply put, if we introduce a bug in one place, and then two different users come to complain, we've violated the principle. It has nothing to do with the number of things we do in our module.

But even now, this rule can do more harm than good. This principle can be understood in as many different ways as there are individuals. A better approach would be to look at how much cognitive load it all creates. It's mentally demanding to remember that change in one place can trigger a chain of reactions across different streams. And that's about it, no fancy terms to learn.

### Too Many Shallow Microservices

This shallow-deep module principle is scale-agnostic, and we can apply it to microservices architecture. Too many shallow microservices won't do any good - the industry is heading towards somewhat "macroservices", i.e., services that are not so shallow (=deep). One of the worst and hardest to fix phenomena is so-called distributed monolith, which is often the result of this overly granular shallow separation.

I once consulted a startup where a team of five developers introduced 17(!) microservices. They were 10 months behind schedule and appeared nowhere close to the public release. Every new requirement led to changes in 4+ microservices. It took an enormous amount of time to reproduce and debug an issue in such a distributed system. Both time to market and cognitive load were unacceptably high. 🤯

Is this the right way to approach the uncertainty of a new system? It's enormously difficult to elicit the right logical boundaries in the beginning. The key is to make decisions as late as you can responsibly wait, because that is when you have the most information at hand. By introducing a network layer up front, we make our design decisions hard to revert right from the start. The team's only justification was: "The FAANG companies proved microservices architecture to be effective". Hello, you got to stop dreaming big.

The Tanenbaum-Torvalds debate argued that Linux's monolithic design was flawed and obsolete, and that a microkernel architecture should be used instead. Indeed, the microkernel design seemed to be superior "from a theoretical and aesthetical" point of view. On the practical side of things - three decades on, microkernel-based GNU Hurd is still in development, and monolithic Linux is everywhere. This page is powered by Linux, your smart teapot is powered by Linux. By monolithic Linux.

A well-crafted monolith with truly isolated modules is often much more flexible than a bunch of microservices. It also requires far less cognitive effort to maintain. It's only when the need for separate deployments becomes crucial, such as scaling the development team, that you should consider adding a network layer between the modules, future microservices.

### Feature-rich Languages

We feel excited when new features got released in our favourite language. We spend some time learning these features, we build code upon them.

If there are lots of features, we may spend half an hour playing with a few lines of code, to use one or another feature. And it's kind of a waste of time. But what's worse, when you come back later, you would have to recreate that thought process!

You not only have to understand this complicated program, you have to understand why a programmer decided this was the way to approach a problem from the features that are available. 🤯

These statements are made by none other than Rob Pike.

> Reduce cognitive load by limiting the number of choices.

Language features are OK, as long as they are orthogonal to each other.

### Business Logic and HTTP Status Codes

On the backend we return:

`401` for expired jwt token
`403` for not enough access
`418` for banned users

The engineers on the frontend use backend API to implement login functionality. They would have to temporarily create the following cognitive load in their brains:

`401` is for expired jwt token  // `[🧠1]`, ok just temporary remember it
`403` is for not enough access  // `[🧠2]`
`418` is for banned users       // `[🧠3]`

Frontend developers would (hopefully) introduce some kind `numeric status -> meaning` dictionary on their side, so that subsequent generations of contributors wouldn't have to recreate this mapping in their brains.

Then QA engineers come into play: "Hey, I got `403` status, is that expired token or not enough access?" QA engineers can't jump straight to testing, because first they have to recreate the cognitive load that the engineers on the backend once created.

Why hold this custom mapping in our working memory? It's better to abstract away your business details from the HTTP transfer protocol, and return self-descriptive codes directly in the response body:

```
{
    "code": "jwt_has_expired"
}
```

Cognitive load on the frontend side: `[🧠0]` (fresh, no facts are held in mind)
Cognitive load on the QA side: `[🧠0]`

The same rule applies to all sorts of numeric statuses (in the database or wherever) - prefer self-describing strings. We are not in the era of 640K computers to optimise for memory.

    People spend time arguing between 401 and 403, making decisions based on their own mental models. New developers are coming in, and they need to recreate that thought process. You may have documented the "whys" (ADRs) for your code, helping newcomers to understand the decisions made. But in the end it just doesn't make any sense. We can separate errors into either user-related or server-related, but apart from that, things are kind of blurry.

It's also often mentally taxing to distinguish between "authentication" and "authorization". We can use simpler terms like "login" and "permissions" to reduce the cognitive load.
