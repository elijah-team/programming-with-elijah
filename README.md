# Blog OS

This repository contains the source code for the _Programming with Elijah_ series at [elijah-team.github.io/programming-with-elijah/](https://elijah-team.github.io/programming-with-elijah/).

If you have questions, open an issue or chat with us [on Gitter](https://gitter.im/nowhere/nowhere).

## Where is the code?

The code for each post lives in a separate git branch. This makes it possible to see the intermediate state after each post.

**The code for the latest post is available [here][latest-post].**

[latest-post]: https://elijah-team.github.io/programming-with-elijah/tree/post-12

You can find the branch for each post by following the `(source code)` link in the [post list](#posts) below. The branches are named `post-XX` where `XX` is the post number, for example `post-03` for the _VGA Text Mode_ post or `post-07` for the _Hardware Interrupts_ post. For build instructions, see the Readme of the respective branch.

You can check out a branch in a subdirectory using [git worktree]:

[git worktree]: https://git-scm.com/docs/git-worktree

```
git worktree add code post-10
```

The above command creates a subdirectory named `code` that contains the code for the 10th post ("Heap Allocation").

## Posts

The goal of this project is to provide step-by-step tutorials in individual blog posts. We currently have the following set of posts:

**Organizing your Code:**

- [Classes](https://elijah-team.github.io/programming-with-elijah/classes/)
    ([source code](https://elijah-team.github.io/programming-with-elijah/tree/post-01))
- [Namespaces and Packages](https://elijah-team.github.io/programming-with-elijah/namespaces-and-packages/)
    ([source code](https://elijah-team.github.io/programming-with-elijah/tree/post-02))
- [Libraries and Executables](https://elijah-team.github.io/programming-with-elijah/libraries-and-executables/)
    ([source code](https://elijah-team.github.io/programming-with-elijah/tree/post-03))
- [Testing](https://elijah-team.github.io/programming-with-elijah/testing/)
    ([source code](https://elijah-team.github.io/programming-with-elijah/tree/post-04))

**The Magic of Functions:**

- [Function Invocation](https://elijah-team.github.io/programming-with-elijah/function-invocation/)
    ([source code](https://elijah-team.github.io/programming-with-elijah/tree/post-05))
- [Double Faults](https://elijah-team.github.io/programming-with-elijah/double-fault-exceptions/)
    ([source code](https://elijah-team.github.io/programming-with-elijah/tree/post-06))
- [Hardware Interrupts](https://elijah-team.github.io/programming-with-elijah/hardware-interrupts/)
    ([source code](https://elijah-team.github.io/programming-with-elijah/tree/post-07))

**The Memory Model:**

- [Introduction to Paging](https://elijah-team.github.io/programming-with-elijah/paging-introduction/)
    ([source code](https://elijah-team.github.io/programming-with-elijah/tree/post-08))
- [Paging Implementation](https://elijah-team.github.io/programming-with-elijah/paging-implementation/)
    ([source code](https://elijah-team.github.io/programming-with-elijah/tree/post-09))
- [Heap Allocation](https://elijah-team.github.io/programming-with-elijah/heap-allocation/)
    ([source code](https://elijah-team.github.io/programming-with-elijah/tree/post-10))
- [Allocator Designs](https://elijah-team.github.io/programming-with-elijah/allocator-designs/)
    ([source code](https://elijah-team.github.io/programming-with-elijah/tree/post-11))

**Concurrency**:

- [Async/Await](https://elijah-team.github.io/programming-with-elijah/async-await/)
    ([source code](https://elijah-team.github.io/programming-with-elijah/tree/post-12))

**Portablility and Code Generation**:

- [Portability and Code Generation](https://elijah-team.github.io/programming-with-elijah/portability-and-code-generation/)
    ([source code](https://elijah-team.github.io/programming-with-elijah/tree/post-12))

## First Edition Posts

The current version of the blog is already the second edition. The first edition is outdated and no longer maintained, but might still be useful. The posts of the first edition are:

<details><summary><i>Click to expand</i></summary>

**Organizing your Code:**

- [A Minimal x86 Kernel](https://elijah-team.github.io/programming-with-elijah/multiboot-kernel.html)
      ([source code](https://elijah-team.github.io/programming-with-elijah/tree/first_edition_post_1))
- [Entering Long Mode](https://elijah-team.github.io/programming-with-elijah/entering-longmode.html)
      ([source code](https://elijah-team.github.io/programming-with-elijah/tree/first_edition_post_2))
- [Set Up Rust](https://elijah-team.github.io/programming-with-elijah/set-up-rust.html)
      ([source code](https://elijah-team.github.io/programming-with-elijah/tree/first_edition_post_3))
- [Printing to Screen](https://elijah-team.github.io/programming-with-elijah/printing-to-screen.html)
      ([source code](https://elijah-team.github.io/programming-with-elijah/tree/first_edition_post_4))

**Memory Management:**

- [Allocating Frames](https://elijah-team.github.io/programming-with-elijah/allocating-frames.html)
      ([source code](https://elijah-team.github.io/programming-with-elijah/tree/first_edition_post_5))
- [Page Tables](https://elijah-team.github.io/programming-with-elijah/modifying-page-tables.html)
      ([source code](https://elijah-team.github.io/programming-with-elijah/tree/first_edition_post_6))
- [Remap the Kernel](https://elijah-team.github.io/programming-with-elijah/remap-the-kernel.html)
      ([source code](https://elijah-team.github.io/programming-with-elijah/tree/first_edition_post_7))
- [Kernel Heap](https://elijah-team.github.io/programming-with-elijah/kernel-heap.html)
      ([source code](https://elijah-team.github.io/programming-with-elijah/tree/first_edition_post_8))

**Exceptions:**

- [Handling Exceptions](https://elijah-team.github.io/programming-with-elijah/handling-exceptions.html)
      ([source code](https://elijah-team.github.io/programming-with-elijah/tree/first_edition_post_9))
- [Double Faults](https://elijah-team.github.io/programming-with-elijah/double-faults.html)
      ([source code](https://elijah-team.github.io/programming-with-elijah/tree/first_edition_post_10))

**Additional Resources:**

- [Cross Compile Binutils](https://elijah-team.github.io/programming-with-elijah/cross-compile-binutils.html)
- [Cross Compile libcore](https://elijah-team.github.io/programming-with-elijah/cross-compile-libcore.html)
- [Set Up GDB](https://elijah-team.github.io/programming-with-elijah/set-up-gdb)
- [Handling Exceptions using Naked Functions](https://elijah-team.github.io/programming-with-elijah/handling-exceptions-with-naked-fns.html)
    - [Catching Exceptions](https://elijah-team.github.io/programming-with-elijah/catching-exceptions.html)
          ([source code](https://elijah-team.github.io/programming-with-elijah/tree/catching_exceptions))
    - [Better Exception Messages](https://elijah-team.github.io/programming-with-elijah/better-exception-messages.html)
          ([source code](https://elijah-team.github.io/programming-with-elijah/tree/better_exception_messages))
    - [Returning from Exceptions](https://elijah-team.github.io/programming-with-elijah/returning-from-exceptions.html)
          ([source code](https://elijah-team.github.io/programming-with-elijah/tree/returning_from_exceptions))

</details>

## License

This project, with exception of the `blog/content` folder, is licensed under either of

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or
  https://www.apache.org/licenses/LICENSE-2.0)
- MIT license ([LICENSE-MIT](LICENSE-MIT) or https://opensource.org/licenses/MIT)

at your option.

For licensing of the `blog/content` folder, see the [`blog/content/README.md`](blog/content/README.md).

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in the work by you, as defined in the Apache-2.0 license, shall be dual licensed as above, without any additional terms or conditions.
