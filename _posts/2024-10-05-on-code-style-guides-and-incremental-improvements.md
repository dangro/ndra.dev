---
title: On code style guides and incremental improvements

layout: post
date: 2024-10-05
author: Daniel
tags:
    - coding
    - style guides
    - innovation
---
In a recent code review, I suggested some changes to improve the accessibility of the feature I was reviewing. The content descriptions for several elements in the user interface were not useful for screen reader users. The author was appreciative of the comments, and they implemented the changes I requested.

However, there was something else in their reply: “I was mostly trying to follow the status quo approach.” That was unexpected, partly because it seemed as if they felt it necessary to justify their original decision.

I thought the comment was unnecessary - I start all code reviews with some assumptions, and one of them is that the code we write is consistent with the code base. If one spends long enough working as a software engineer, one converges on this practice and writes code that is consistent with whatever styleguide or coding standard is used in the code. This does not happen by accident as, generally, early in our careers, it is ingrained in us that consistent style is important as it makes code easier to understand. Computers execute code, but it is still read and written (mostly) by people.

Consider the following excerpts from the Google and Python coding style guides:

> Every major open-source project has its own style guide: a set of conventions (sometimes arbitrary) about how to write code for that project. It is much easier to understand a large codebase when all the code in it is in a consistent style. [^1]

> A style guide is about consistency. Consistency with this style guide is important. Consistency within a project is more important. Consistency within one module or function is the most important. [^2]

And so, we aim to replicate the same patterns we see in the codebase. I like this as it means it is one set of decisions I don't have to worry about in most cases. But this only works if we continuously learn and refine our craft.

With experience, we understand the unwritten parts of the style guide and learn to identify the exceptions and recognize the smelly parts of the code. In this particular case, the code was initially written without regard for accessibility, and in the quest to keep the code consistent, no one ever challenged it.

In a quest for consistency, we are forsaking incremental improvements and even innovation by trying not to stand out and instead write code that looks exactly as if it has always been there.

We use our experience and best judgment to determine the most effective way to deliver value. Sometimes, that means we must resist the urge to refactor code; on other occasions, we have the liberty to tear down old artifacts. Whatever we do, we must remain vigilant and do the right thing when it counts. Python's style guide offers wise advice:

> However, know when to be inconsistent—sometimes style guide recommendations just aren't applicable. When in doubt, use your best judgment. Look at other examples and decide what looks best. And don’t hesitate to ask! [^2]

If the style guide isn't empowering people to improve the products we build, then perhaps it is time to change it.

[^1]: https://google.github.io/styleguide/
[^2]: https://pep8.org/




