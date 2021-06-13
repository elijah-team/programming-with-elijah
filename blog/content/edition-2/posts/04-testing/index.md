+++
title = "Testing"
weight = 4
path = "testing"
date = 2019-04-27

[extra]
chapter = "Organizing your Code"
+++

This post explores unit and integration testing in `no_std` executables. We will use Rust's support for custom test frameworks to execute test functions inside our kernel. To report the results out of QEMU, we will use different features of QEMU and the `bootimage` tool.

<!-- more -->

This blog is openly developed on [GitHub]. If you have any problems or questions, please open an issue there. You can also leave comments [at the bottom]. The complete source code for this post can be found in the [`post-04`][post branch] branch.

[GitHub]: https://github.com/elijah-team/programming-with-elijah/
[at the bottom]: #comments
[post branch]: https://elijah-team.github.io/programming-with-elijah/tree/post-04

<!-- toc -->

## Requirements


## Testing in Rust

Since the `test` crate depends on the standard library, it is not available for our bare metal target. While porting the `test` crate to a `#[no_std]` context [is possible][utest], it is highly unstable and requires some hacks such as redefining the `panic` macro.

[utest]: https://github.com/japaric/utest

### Custom Test Frameworks


<div class = "warning">

**Note:** There is currently a bug in cargo that leads to "duplicate lang item" errors on `cargo test` in some cases. It occurs when you have set `panic = "abort"` for a profile in your `Cargo.toml`. Try removing it, then `cargo test` should work. See the [cargo issue](https://github.com/rust-lang/cargo/issues/7359) for more information on this.

</div>


## Exiting QEMU

### I/O Ports

## Summary

Testing is a very useful technique to ensure that certain components have a desired behavior. Even if they cannot show the absence of bugs, they're still an useful tool for finding them and especially for avoiding regressions.

This post explained how to set up a test framework for our Rust kernel. We used the custom test frameworks feature of Rust to implement support for a simple `#[test_case]` attribute in our bare-metal environment. By using the `isa-debug-exit` device of QEMU, our test runner can exit QEMU after running the tests and report the test status out. To print error messages to the console instead of the VGA buffer, we created a basic driver for the serial port.

After creating some tests for our `println` macro, we explored integration tests in the second half of the post. We learned that they live in the `tests` directory and are treated as completely separate executables. To give them access to the `exit_qemu` function and the `serial_println` macro, we moved most of our code into a library that can be imported by all executables and integration tests. Since integration tests run in their own separate environment, they make it possible to test interactions with the hardware or to create tests that should panic.

We now have a test framework that runs in a realistic environment inside QEMU. By creating more tests in future posts, we can keep our kernel maintainable when it becomes more complex.

## What's next?

In the next post, we will explore _CPU exceptions_. These exceptions are thrown by the CPU when something illegal happens, such as a division by zero or an access to an unmapped memory page (a so-called “page fault”). Being able to catch and examine these exceptions is very important for debugging future errors. Exception handling is also very similar to the handling of hardware interrupts, which is required for keyboard support.
