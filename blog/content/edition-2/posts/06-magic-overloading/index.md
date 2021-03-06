+++
title = "Overloading"
weight = 6
path = "overloading"
date  = 2021-06-29

[extra]
chapter = "The Magic of Functions"
+++

This post explores the opportunites that Elijah gives you, the programmer, to overload or override functions. It also specifies where this behavior is not allowed.

<!-- more -->

This blog is openly developed on [GitHub]. If you have any problems or questions, please open an issue there. You can also leave comments [at the bottom].  The complete source code for this post can be found in the [`post-06`][post branch] branch.

[GitHub]: https://github.com/elijah-team/programming-with-elijah/
[at the bottom]: #comments
[post branch]: https://elijah-team.github.io/programming-with-elijah/tree/post-06

<!-- toc -->

## Overloading Operators

Overloading operators is done in the style of Python.  You define a special function (dunder method) for the operator you wish to chnage.  This is useful when you would like to improve the readability of your code for basic operations.

Overloaded operators can be defined in the class, in another class in reverse or in a namespace (usually the global or module ones).

The names of the _dunder_ methods follow:

Operator | Function Name
:-------:|:-------------:
 `+`     |  `__add__`
 `-`     |  `__sub__`
 `*`     |  `__mul__`
 `/`     |  `__div__`
 `<`     |  `__lt__`
 `<=`    |  `__le__`
 `>`     |  `__gt__`
 `>=`    |  `__ge__`
 `==`    |  `__eq__`
 `!=`    |  `__ne__`

This is not an exhaustive list.

## Overloading Functions

Overloading functions is a feature from C++ and Java (and distinctly not from Python and other dynamic languages) that says that you can have multiple functions with the same name that differ only in the number of arguments or just the type of arguments.  This is useful when you want to do the same thing, but to different things, for example.

## Overloading Constructors

Overloading constructors is basically the same as overloading functions.  You can have multiple constructors that differ only in the number of arguments or just the type of arguments.

## Not overloading (named) constructors

Named constructors cannot be overloaded.  That is only one per name per class is allowed.  Of course you can choose to inherit or redefine a named constructor from a base class.

## What's next?
The next post explains how ...