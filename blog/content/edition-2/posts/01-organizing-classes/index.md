+++
title = "Classes"
weight = 1
path = "classes"
date = 2021-06-13
 
[extra]
chapter = "Organizing your Code"
+++

Classes are one of the fundamental building blocks of Elijah code.  This post will discuss the kinds of classes available in Elijah.

<!-- more -->

This blog is openly developed on [GitHub]. If you have any problems or questions, please open an issue there. You can also leave comments [at the bottom]. The complete source code for this post can be found in the [`post-01`][post branch] branch.

[GitHub]: https://github.com/elijah-team/programming-with-elijah/
[at the bottom]: #comments
[post branch]: https://elijah-team.github.io/programming-with-elijah/tree/post-01

<!-- toc -->

## Overview 

From the Python documentation:

> Classes provide a means of bundling data and functionality together. Creating a new class creates a new type of object, allowing new instances of that type to be made. Each class instance can have attributes attached to it for maintaining its state. Class instances can also have methods (defined by its class) for modifying its state.

All classes support multiple inheritance.  Redefinition/renaming of conflicting features (variables, properties and functions) is a "research topic".

All classes support nesting and can refer to the contents of its container, where applicable (basically in normal classes).

## Normal Classes

A normal class is just that -- normal.  It can be _generic_, but other than that it has no other special behavior in the system.  Classes are the "containers" and an organizational structure for variables and functions.  Special to classes are properties, which are basically functions that look like variables.

To interact with a class, you have to create an _instance_, by _constructing_ it. See _constructors_.

Classes are also special because they also represent _types_.  All values (variables and expressions) in Elijah have a type, which frequently is not specified, but automatically found out by a process known as _type deduction_.  This is functinonally similar to _type inferencing_.

## Interface Classes

An interface class declares a class that can't be instantiated.  The purpose of it is to specify a set of functions (and/or properties) which must be implemented by derived classes.  An interface can extend another interface by inheriting from it.  An interface can combine multiple interfaces into a single interface if thata is the programmer's wish.

An interface can contain default behavior (as Java was recently extended to implement) for functions that can be inherited or overridden by derived classes.

> An interface can override its inherited default behaviors too.

An interface can contain properties, which can be `abstract`.  They usually are because properties usually utilize the member variables of a class.
An interface cannot contain variables or abstract methods.  An interface usually contains just function headers.

## Signature Classes

A signature class can only contain function headers.  That means _contracts_ are not supported, and neither is the default specification of behaviors.  It only exists at compile time and cannot be tested for (using `is_a`).  It's purpose is to specify a set of functions that must be implemeted by derived classes.  It is kind of like pattern matching for classes.

> Maybe we can relax the can't be tested for thing...

## Abstract Classes

Abstract classes extend the conception of interfaces by allowing the specification of functions with _contracts_ but no implementation (meaning they are abstract) and allowing the inclusion of variables and non-abstract properties.

An abstract class is meant to define default behavior for a set of derived classes.

An abstract class cannot be instantiated.

## Enum Classes

Enums exist to group the possible states of a variable.  Enums are very similar to `datatype`s and very similar to classes and can be looked at as the combination of the two.

`enum` classes in Elijah are the same as they are in Java.  Each variant can contain a number of attributes or none at all (but it is an all or  nothing choice, unlike `datatypes`).  Also each variant can contain implementations of abstract methods defined in the body of the enum itself, thus allowing the differentiation of variant states without defining functions in a separate namespace.  

Enums can contain only one constructor and only one named constructor called copy, which would take a single value of the same enum type.

## Datatypes

A datatype is an enumeration of known states.  In fact, in Rust, it is called an `enum`.  

Datatypes have a special syntax:

```
datatype Boolean = 
  True
  | False
```

That is, they do not allow the definition of functions alongside of the rest of the declaration.  Functions which take a `datatype` as `self` are rare because they are usually used in pattern matching in `match` clauses.  But it is customary to declare those functions that do in a parallel namespace with an underscore affixed.

Datatypes allow data to be attached to instances.  Instances are only created when there is data to be attached.  `True` and `False` above are singletons, and may be represented as integers by the compiler.

```
datatype Maybe[T] = 
  Some(t: T)
  | Nothing
```
> Note this type is _generic_

Datatypes are immutable, that is, once created, their values cannot be changed.

This says either you have `Some` value `t` of generic type `T`, or you have `Nothing`.  Note that `t` cannot be assigned to -- it's value can never be changed.

Datatypes can also have "universal" attributes -- these values are present in all variants of the datatype.

```
datatype Message(id: Integer32) {
  Quit
  | Move ( x: i32, y: i32 )
  | Write(String)
  | ChangeColor(i32, i32, i32)
}
```

Note that all variants have and `id` attribute, and each variant has a different number of individual attrbutes.

## Annotation Classes

Annotations are declared by inheriting from `tripleo.lang.Annotation`. I don't want to use a keyword for this right now.
I don't know what effect annotations will have on the code produced by the Elijah compiler.


## Exception Classes

Exceptions are declared by inheriting from `tripleo.lang.Exception`. I don't want to use a keyword for this right now.
For Java interopability, you can use the annotation `ExceptionType(Error | Throwable)`


```
rustup target add thumbv7em-none-eabihf
```

This downloads a copy of the standard (and core) library for the system. Now we can build our freestanding executable for this target:

```
cargo build --target thumbv7em-none-eabihf
```

## Summary

There are a number of different types of classes in Elijah, and some of them overlap, but they are for different programming styles or tastes.  Each has its benefits and each has its purpose.  To effectively program in Elijah it is necessary to master each one.

## What's next?

The [next post] how to organize classes to make them part of a cohesive whole.

[next post]: @/edition-2/posts/02-namespaces-and-packages/index.md
