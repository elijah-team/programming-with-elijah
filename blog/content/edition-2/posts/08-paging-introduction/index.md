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

## Allocators

Each function has an implicit allocator (which is usually inherited from somewhere, like the next function up in the call stack).  It is this allocator that determines the memory profile of the function.

That means you can have a separate arena for GCed objects or a Pool for efficient use of memory without touching `malloc`.

## What's next?

The next post explains how to implement support for paging in our kernel. It presents different ways to access physical memory from our kernel, which makes it possible to access the page tables that our kernel runs on. At this point we are able to implement functions for translating virtual to physical addresses and for creating new mappings in the page tables.
