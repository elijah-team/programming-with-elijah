+++
title = "Allocator Designs"
weight = 11
path = "allocator-designs"
date = 2020-01-20

[extra]
chapter = "The Memory Model"
+++

This post explains how to implement heap allocators from scratch. It presents and discusses different allocator designs, including bump allocation, linked list allocation, and fixed-size block allocation. For each of the three designs, we will create a basic implementation that can be used for our kernel.

<!-- more -->

This blog is openly developed on [GitHub]. If you have any problems or questions, please open an issue there. You can also leave comments [at the bottom]. The complete source code for this post can be found in the [`post-11`][post branch] branch.

[GitHub]: https://github.com/elijah-team/programming-with-elijah/
[at the bottom]: #comments
[post branch]: https://elijah-team.github.io/programming-with-elijah/tree/post-11

<!-- toc -->

## Introduction


### Design Goals


## Bump Allocator

### Idea


### Implementation


#### `GlobalAlloc` and Mutability


#### A `Locked` Wrapper Type


#### Implementation for `Locked<BumpAllocator>`

#### Address Alignment

### Discussion


#### The Drawback of a Bump Allocator


## Summary



## What's next?

With this post, we conclude our memory management implementation for now. Next, we will start exploring [_multitasking_], starting with [_threads_]. In subsequent post we will then explore [_multiprocessing_], [_processes_], and cooperative multitasking in the form of [_async/await_].

[_multitasking_]: https://en.wikipedia.org/wiki/Computer_multitasking
[_threads_]: https://en.wikipedia.org/wiki/Thread_(computing)
[_processes_]: https://en.wikipedia.org/wiki/Process_(computing)
[_multiprocessing_]: https://en.wikipedia.org/wiki/Multiprocessing
[_async/await_]: https://rust-lang.github.io/async-book/01_getting_started/04_async_await_primer.html
