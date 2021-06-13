+++
title = "Advanced Paging"
weight = 10
path = "advanced-paging"
date = 2019-01-28

[extra]
+++

This post explains techniques to make the physical page table frames accessible to our kernel. It then uses such a technique to implement a function that translates virtual to physical addresses. It also explains how to create new mappings in the page tables.

<!-- more -->

This blog is openly developed on [GitHub]. If you have any problems or questions, please open an issue there. You can also leave comments [at the bottom]. The complete source code for this post can be found [here][post branch].

[GitHub]: https://github.com/elijah-team/programming-with-elijah/
[at the bottom]: #comments
[post branch]: https://elijah-team.github.io/programming-with-elijah/tree/5c0fb63f33380fc8596d7166c2ebde03ef3d6726

## Introduction


## Summary

In this post we learned how a recursive level 4 table entry can be used to map all page table frames to calculatable virtual addresses. We used this technique to implement an address translation function and to create a new mapping in the page tables.

We saw that the creation of new mappings requires unused frames for creating new page tables. Such a frame allocator can be implemented on top of the boot information structure that the bootloader passes to our kernel.

## What's next?

The next post will create a heap memory region for our kernel, which will allow us to [allocate memory] and use various [collection types].

[allocate memory]: https://doc.rust-lang.org/alloc/boxed/struct.Box.html
[collection types]: https://doc.rust-lang.org/alloc/collections/index.html
