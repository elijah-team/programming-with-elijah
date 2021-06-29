+++
title = "Memory Classes"
weight = 8
path = "memory-classes"
date = 2021-06-29

[extra]
chapter = "The Memory Model"
+++

Memory in Elijah is under complete control of the programmer. (This may not be so in some backends such as Java, where there is only a modicum of control allowed.)  Memory models, when applied to variables allow the specification of how and when memory is allocated and released by a program.

<!-- more -->

## Memory Classes

* ref 
* gc 
* pooled 
* manual

## Reference Counting

From [Wikipedia](https://en.wikipedia.org/wiki/Reference_counting):

> _Reference counting_ is a programming technique of storing the number of references, pointers, or handles to an object (aka a block of memory).
> 
> In garbage collection algorithms, reference counts may be used to deallocate objects that are no longer needed. 

## Automatic Garbage Collection

> A garbage collector (GC) cleans up the memory when objects you allocated in your code become obsolete.

The current implementation of Elijah uses the Boehm collector (libgc).

## Pooled Memory

A memory pool avoids the system allocator (`malloc`) when it is used right.  When it is used wrong it just wastes memory.

## Manual

This is the equivalent of just using `malloc` and `free`, or `new` and `delete`.

## Allocators

Each function has an implicit allocator (which is usually inherited from somewhere, like the next function up in the call stack).  It is this allocator that determines the memory profile of the function.

That means you can have a separate arena for GCed objects or a Pool for efficient use of memory without touching `malloc`.

## Finalizers and Destrtuctors

Nothing to say yet

## What's next?

The next post explains how to ...