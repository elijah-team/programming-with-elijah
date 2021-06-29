+++
title = "Libraries and Executables"
weight = 3
path = "libraries-and-executables"
date  = 2021-06-13

[extra]
chapter = "Organizing your Code"
+++

Building and publishing your software is only possible if the compiler knows how to find it.  Below, find an overview of the `.ez` file format.

<!-- more -->

This blog is openly developed on [GitHub]. If you have any problems or questions, please open an issue there. You can also leave comments [at the bottom]. The complete source code for this post can be found in the [`post-03`][post branch] branch.

[GitHub]: https://github.com/elijah-team/programming-with-elijah/
[at the bottom]: #comments
[post branch]: https://elijah-team.github.io/programming-with-elijah/tree/post-03

<!-- toc -->

## Overview

Elijah "program text" is contained in "modules".  Some languages call them "compilation units".  Either way, a module consists of `import` statements, `alias` statements, classes and namespaces, among other things.

> A module is just a fancy name for a file, unless you're using [scid][_Source code as a Database_].

[scid]: http://wiki.c2.com/?SourceCodeInDatabase

But unlike some other languages you don't specify files to compile on the command line (or in your make tool, which in Elijah's case, happens to be integraeted with the compiler).  You specify an `.ez` file that tells the compiler two things: where to find your code, and a little about how to generate it.


## Summary
In this post we learned about the structure of the VGA text buffer and how it can be written through the memory mapping at address `0xb8000`. We created a Rust module that encapsulates the unsafety of writing to this memory mapped buffer and presents a safe and convenient interface to the outside.

We also saw how easy it is to add dependencies on third-party libraries, thanks to cargo. The two dependencies that we added, `lazy_static` and `spin`, are very useful in OS development and we will use them in more places in future posts.

## What's next?
The next post explains how to set up Rust's built in unit test framework. We will then create some basic unit tests for the VGA buffer module from this post.
