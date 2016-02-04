# The rustc driver

The driver coordinates the [compilation phases][comp_phases]. It handles all
the high-level coordination of the compilation process. It deals with
handling command-line arguments, maintaining compilation state, and invoking
each phase of compilation.

The driver also provides an API to allow for customization of the compilation
process. There are two main means of customization, high-level control of the
driver using [`CompilerCalls`] and controlling each phase of compilation using a
[`CompilerController`].

These APIs can be used to create a "drop-in" compiler. That is, a tool which
can be used in all the ways in which `rustc` can be used. This could be a tool
like `rustdoc`, or `rustfmt`, or a customized compiler which adds extra code
generation or analysis phases. Using the driver APIs to create a drop-in
replacement for `rustc` is much easier than forking the compiler and keeping
it up to date as it evolves upstream.

## `CompilerCalls`

This is a trait that you can implement in your tool in order to hook in to the
process of processing command line arguments and driving the compiler.

## `CompilerController`

This is a struct consisting of `PhaseController`s and flags.

[comp_phases]: #
