+++
title = "Portability and Code Generation"
weight = 12
path = "portability-and-code-generation"
date = 2020-03-27

[extra]
chapter = "Portability and Code Generation"
+++

In this post we explore _cooperative multitasking_ and the _async/await_ feature of Rust. We take a detailed look how async/await works in Rust, including the design of the `Future` trait, the state machine transformation, and _pinning_. We then add basic support for async/await to our kernel by creating an asynchronous keyboard task and a basic executor.

<!-- more -->

This blog is openly developed on [GitHub]. If you have any problems or questions, please open an issue there. You can also leave comments [at the bottom]. The complete source code for this post can be found in the [`post-12`][post branch] branch.

[GitHub]: https://github.com/elijah-team/programming-with-elijah/
[at the bottom]: #comments
[post branch]: https://elijah-team.github.io/programming-with-elijah/tree/post-12

<!-- toc -->

## Summary

We started this post by introducing **multitasking** and differentiating between _preemptive_ multitasking, which forcibly interrupts running tasks regularly, and _cooperative_ multitasking, which lets tasks run until they voluntarily give up control of the CPU.

We then explored how Rust's support of **async/await** provides a language-level implementation of cooperative multitasking. Rust bases its implementation on top of the polling-based `Future` trait, which abstracts asynchronous tasks. Using async/await, it is possible to work with futures almost like with normal synchronous code. The difference is that asynchronous functions return a `Future` again, which needs to be added to an executor at some point in order to run it.

Behind the scenes, the compiler transforms async/await code to _state machines_, with each `.await` operation corresponding to a possible pause point. By utilizing its knowledge about the program, the compiler is able to save only the minimal state for each pause point, resulting in a very small memory consumption per task. One challenge is that the generated state machines might contain _self-referential_ structs, for example when local variables of the asynchronous function reference each other. To prevent pointer invalidation, Rust uses the `Pin` type to ensure that futures cannot be moved in memory anymore after they have been polled for the first time.

For our **implementation**, we first created a very basic executor that polls all spawned tasks in a busy loop without using the `Waker` type at all. We then showed the advantage of waker notifications by implementing an asynchronous keyboard task. The task defines a static `SCANCODE_QUEUE` using the mutex-free `ArrayQueue` type provided by the `crossbeam` crate. Instead of handling keypresses directly, the keyboard interrupt handler now puts all received scancodes in the queue and then wakes the registered `Waker` to signal that new input is available. On the receiving end, we created a `ScancodeStream` type to provide a `Future` resolving to the next scancode in the queue. This made it possible to create an asynchronous `print_keypresses` task that uses async/await to interpret and print the scancodes in the queue.

To utilize the waker notifications of the keyboard task, we created a new `Executor` type that uses an `Arc`-shared `task_queue` for ready tasks. We implemented a `TaskWaker` type that pushes the ID of woken tasks directly to this `task_queue`, which are then polled again by the executor. To save power when no tasks are runnable, we added support for putting the CPU to sleep using the `hlt` instruction. Finally, we discussed some potential extensions of our executor, for example for providing multi-core support.

## What's Next?

Using async/wait, we now have basic support for cooperative multitasking in our kernel. While cooperative multitasking is very efficient, it leads to latency problems when individual tasks keep running for too long and thus prevent other tasks to run. For this reason, it makes sense to also add support for preemptive multitasking to our kernel.

In the next post, we will introduce _threads_ as the most common form of preemptive multitasking. In addition to resolving the problem of long running tasks, threads will also prepare us for utilizing multiple CPU cores and running untrusted user programs in the future.
