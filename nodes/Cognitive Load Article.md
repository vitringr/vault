---
tags:
  - "article"
context:
  - "[[Software Design]]
  - "[[Software Architecture]]
---

# Cognitive Load Article

Reference: [Cognitive Load](https://github.com/zakirullin/cognitive-load)

---

Cognitive load in software is how much a developer needs to think in order to complete a task.

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

## Complex Conditionals

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

## Nested ifs

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

## Inheritance Nightmare

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

### Too Many Small Methods, Classes or Modules

_Method, class and module are interchangeable in this context._

Mantras like "methods should be shorter than 15 lines of code" or "classes should be small" turned out to be somewhat wrong.

**Deep Module**: Simple interface, complex functionality
**Shallow Module**: Interface is relatively complex to the small functionality it provides

Having too many shallow modules can make it difficult to understand the project. Not only do we have to keep in mind each module responsibilities, but also all their interactions. To understand the purpose of a shallow module, we first need to look at the functionality of all the related modules. Jumping between such shallow components is mentally exhausting, linear thinking is more natural to us humans.

> Information hiding is paramount, and we don't hide as much complexity in shallow modules.

I have two pet projects, both of them are somewhat 5K lines of code. The first one has 80 shallow classes, whereas the second one has only 7 deep classes. I haven't been maintaining any of these projects for one year and a half.

Once I came back, I realised that it was extremely difficult to untangle all the interactions between those 80 classes in the first project. I would have to rebuild an enormous amount of cognitive load before I could start coding. On the other hand, I was able to grasp the second project quickly, because it had only a few deep classes with a simple interface.

> The best components are those that provide powerful functionality yet have a simple interface.

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

All too often, we end up creating lots of shallow modules, following some vague "a module should be responsible for one, and only one, thing" principle. What is this blurry one thing? Instantiating an object is one thing, right? So `MetricsProviderFactoryFactory` seems to be just fine. The names and interfaces of such classes tend to be more mentally taxing than their entire implementations, what kind of abstraction is that? Something went wrong. 

We make changes to our systems to satisfy our users and stakeholders. We are responsible to them. 

> A module should be responsible to one, and only one, user or stakeholder.

This is what this [[Single Responsibility Principle]] is all about. Simply put, if we introduce a bug in one place, and then two different business people come to complain, we've violated the principle. It has nothing to do with the number of things we do in our module.

But even now, this rule can do more harm than good. This principle can be understood in as many different ways as there are individuals. A better approach would be to look at how much cognitive load it all creates. It's mentally demanding to remember that change in one place can trigger a chain of reactions across different business streams. And that's about it, no fancy terms to learn.

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

#### Thoughts from an engineer with 20 years of C++ experience

I was looking at my RSS reader the other day and noticed that I have somewhat three hundred unread articles under the "C++" tag. I haven't read a single article about the language since last summer, and I feel great!

I've been using C++ for 20 years for now, that's almost two-thirds of my life. Most of my experience lies in dealing with the darkest corners of the language (such as undefined behaviours of all sorts). It's not a reusable experience, and it's kind of creepy to throw it all away now.

Like, can you imagine, the token `||` has a different meaning in `requires ((!P<T> || !Q<T>))` and in `requires (!(P<T> || Q<T>))`. The first is the constraint disjunction, the second is the good-old logical `or` operator, and they behave differently.

You can't allocate space for a trivial type and just `memcpy` a set of bytes there without extra effort - that won't start the lifetime of an object. This was the case before C++20. It was fixed in C++20, but the cognitive load of the language has only increased.

Cognitive load is constantly growing, even though things got fixed. I should know what was fixed, when it was fixed, and what it was like before. I am a professional after all. Sure, C++ is good at legacy support, which also means that you will face that legacy. For example, last month a colleague of mine asked me about some behaviour in C++03.

There were 20 ways of initialization. Uniform initialization syntax has been added. Now we have 21 ways of initialization. By the way, does anyone remember the rules for selecting constructors from the initializer list? Something about implicit conversion with the least loss of information, but if the value is known statically, then...

This increased cognitive load is not caused by a business task at hand. It is not an intrinsic complexity of the domain. It is just there due to historical reasons (extraneous cognitive load).

I had to come up with some rules. Like, if that line of code is not as obvious and I have to remember the standard, I better not write it that way. The standard is somewhat 1500 pages long, by the way.

By no means I am trying to blame C++. I love the language. It's just that I am tired now.

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

P.S. It's often mentally taxing to distinguish between "authentication" and "authorization". We can use simpler terms like "login" and "permissions" to reduce the cognitive load.

### Abusing DRY Principle

Do not repeat yourself - that is one of the first principles you are taught as a software engineer. It is so deeply embedded in ourselves that we can not stand the fact of a few extra lines of code. Although in general a good and fundamental rule, when overused it leads to the cognitive load we can not handle.

Nowadays, everyone builds software based on logically separated components. Often those are distributed among multiple codebases representing separate services. When you strive to eliminate any repetition, you might end up creating tight coupling between unrelated components. As a result changes in one part may have unintended consequences in other seemingly unrelated areas. It can also hinder the ability to replace or modify individual components without impacting the entire system.

In fact, the same problem arises even within a single module. You might extract common functionality too early, based on perceived similarities that might not actually exist in the long run. This can result in unnecessary abstractions that are difficult to modify or extend.

> A little copying is better than a little dependency.

We are tempted to not reinvent the wheel so strong that we are ready to import large, heavy libraries to use a small function that we could easily write by ourselves.

**All your dependencies are your code**. Going through 10+ levels of stack trace of some imported library and figuring out what went wrong (because things go wrong) is painful.

### Tight Coupling With a Framework

There's a lot of "magic" in frameworks. By relying too heavily on a framework, we force all upcoming developers to learn that "magic" first. It can take months. Even though frameworks enable us to launch MVPs in a matter of days, in the long run they tend to add unnecessary complexity and cognitive load.

Worse yet, at some point frameworks can become a significant constraint when faced with a new requirement that just doesn't fit the architecture. From here onwards people end up forking a framework and maintaining their own custom version. Imagine the amount of cognitive load a newcomer would have to build (i.e. learn this custom framework) in order to deliver any value.

**By no means do we advocate to invent everything from scratch!**

We can write code in a somewhat framework-agnostic way. The business logic should not reside within a framework; rather, it should use the framework's components. Put a framework outside of your core logic. Use the framework in a library-like fashion. This would allow new contributors to add value from day one, without the need of going through debris of framework-related complexity first.

[[Why I Hate Frameworks Article]]

### Layered Architecture

There is a certain engineering excitement about all this stuff.

I myself was a passionate advocate of Hexagonal/Onion Architecture for years. I used it here and there and encouraged other teams to do so. The complexity of our projects went up, the sheer number of files alone had doubled. It felt like we were writing a lot of glue code. On ever changing requirements we had to make changes across multiple layers of abstractions, it all became tedious.

Abstraction is supposed to hide complexity, here it just adds indirection. Jumping from call to call to read along and figure out what goes wrong and what is missing is a vital requirement to quickly solve a problem. With this architecture’s layer uncoupling it requires an exponential factor of extra, often disjointed, traces to get to the point where the failure occurs. Every such trace takes space in our limited working memory.

This architecture was something that made intuitive sense at first, but every time we tried applying it to projects it made a lot more harm than good. In the end, we gave it all up in favour of the good old dependency inversion principle. No port/adapter terms to learn, no unnecessary layers of horizontal abstractions, no extraneous cognitive load.

If you think that such layering will allow you to quickly replace a database or other dependencies, you're mistaken. Changing the storage causes lots of problems, and believe us, having some abstractions for the data access layer is the least of your worries. At best, abstractions can save somewhat 10% of your migration time (if any), the real pain is in data model incompatibilities, communication protocols, distributed systems challenges, and implicit interfaces.

> With a sufficient number of users of an API,
> it does not matter what you promise in the contract:
> all observable behaviors of your system
> will be depended on by somebody.

So, why pay the price of high cognitive load for such a layered architecture, if it doesn't pay off in the future? Plus, in most cases, that future of replacing some core component never happens.

These architectures are not fundamental, they are just subjective, biased consequences of more fundamental principles. Why rely on those subjective interpretations? Follow the fundamental rules instead: dependency inversion principle, single source of truth, cognitive load and information hiding. Your business logic should not depend on low-level modules like database, UI or framework. We should be able to write tests for our core logic without worrying about the infrastructure, and that's it.

Do not add layers of abstractions for the sake of an architecture. Add them whenever you need an extension point that is justified for practical reasons.

Layers of abstraction aren't free of charge, they are to be held in our limited working memory.

### Domain-driven design

Domain-driven design has some great points, although it is often misinterpreted. People say, "We write code in DDD", which is a bit strange, because DDD is more about the problem space rather than the solution space.

Ubiquitous language, domain, bounded context, aggregate, event storming are all about problem space. They are meant to help us learn the insights about the domain and extract the boundaries. DDD enables developers, domain experts and business people to communicate effectively using a single, unified language. Rather than focusing on these problem space aspects of DDD, we tend to emphasise particular folder structures, services, repositories, and other solution space techniques.

Chances are that the way we interpret DDD is likely to be unique and subjective. And if we build code upon this understanding, i.e., if we create a lot of extraneous cognitive load - future developers are doomed. 🤯

Team Topologies provides a much better, easier to understand framework that helps us split the cognitive load across teams. Engineers tend to develop somewhat similar mental models after learning about Team Topologies. DDD, on the other hand, seems to be creating 10 different mental models for 10 different readers. Instead of being common ground, it becomes a battleground for unnecessary debates.

### Cognitive Load in Familiar Projects

> The problem is that familiarity is not the same as simplicity. They feel the same — that same ease of moving through a space without much mental effort — but for very different reasons. Every “clever” (read: “self-indulgent”) and non-idiomatic trick you use incurs a learning penalty for everyone else. Once they have done that learning, then they will find working with the code less difficult. So it is hard to recognise how to simplify code that you are already familiar with. This is why I try to get “the new kid” to critique the code before they get too institutionalised!
>
> It is likely that the previous author(s) created this huge mess one tiny increment at a time, not all at once. So you are the first person who has ever had to try to make sense of it all at once.
>
> In my class I describe a sprawling SQL stored procedure we were looking at one day, with hundreds of lines of conditionals in a huge WHERE clause. Someone asked how anyone could have let it get this bad. I told them: “When there are only 2 or 3 conditionals, adding another one doesn’t make any difference. By the time there are 20 or 30 conditionals, adding another one doesn’t make any difference!”
>
> There is no “simplifying force” acting on the code base other than deliberate choices that you make. Simplifying takes effort, and people are too often in a hurry.

If you've internalized the mental models of the project into your long-term memory, you won't experience a high cognitive load.

The more mental models there are to learn, the longer it takes for a new developer to deliver value.

Once you onboard new people on your project, try to measure the amount of confusion they have (pair programming may help). If they're confused for more than ~40 minutes in a row - you've got things to improve in your code.

If you keep the cognitive load low, people can contribute to your codebase within the first few hours of joining your company.

### Examples

- Our architecture is a standard CRUD app architecture, a Python monolith on top of Postgres.
- How Instagram scaled to 14 million users with only 3 engineers.
- The companies where we were like ”woah, these folks are smart as hell” for the most part failed.

These architectures are quite boring and easy to understand. Anyone can grasp them without much mental effort.

Involve junior developers in architecture reviews. They will help you to identify the mentally demanding areas.

Maintaining software is hard, things break and we would need every bit of mental effort we can save.

## Conclusion

Imagine for a moment that what we inferred in the second chapter isn’t actually true. If that’s the case, then the conclusion we just negated, along with the conclusions in the previous chapter that we had accepted as valid, might not be correct either.

Do you feel it? Not only do you have to jump all over the article to get the meaning (shallow modules!), but the paragraph in general is difficult to understand. We have just created an unnecessary cognitive load in your head. Do not do this to your colleagues.

We should reduce any cognitive load above and beyond what is intrinsic to the work we do.
