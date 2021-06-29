+++
title = "Namespaces and Packages"
weight = 2
path = "namespaces-and-packages"
date = 2021-06-13

[extra]
chapter = "Organizing your Code"
+++

Namespaces and packages are essential to keep your code orderly and to use code written by other people.

<!-- more -->

This blog is openly developed on [GitHub]. If you have any problems or questions, please open an issue there. You can also leave comments [at the bottom]. The complete source code for this post can be found in the [`post-02`][post branch] branch.

[GitHub]: https://github.com/elijah-team/programming-with-elijah/
[at the bottom]: #comments
[post branch]: https://elijah-team.github.io/programming-with-elijah/tree/post-02

<!-- toc -->

## Namespaces

_Namespaces_ are an idea from C++ (and C# admittedly), originally intended only to support the production and use of C functions without name mangling.  Now this was before annotations, so bear with me.  They are still used for that purpose, but can serve a dual role as an organizer of code.

See, namespaces are singletons.  Some people don't like singletons (and they are hard to mock), but, nevertheless, they made it into the language.  

Namespaces can be normal or instance.  Instance namespaces are created on first access, similar to how static classes work in Java.  This feature was added to solve the non-deterministic creation problem -- normal namespaces are created at program invocation (start) in what may not always be the same order.  This is not always important, and there are other ways around this, but instance namespaces are the simplest.

It would seem that namespaces perform the same duty as packages, but namespaces in Elijah are mainly used for grouping of functionality and information hiding.  They also perform the same function as static (or class in Smalltalk) members in other languages.

## Packages

Packages are ripped straight from Java.  They are the top level of organization in a module (or file).  

More...

## Imports

...

## What's next?

In the next post, we will explore the VGA text buffer in more detail and write a safe interface for it. We will also add support for the `println` macro.
