# Rust Features

Rust is a programming language built to be fast, secure and reliable.

Rust is a statically and strongly typed systems programming language.

Statically typed means all types are known at compile-time. Strongly typed means types are designed to make it harder to write incorrect programs.

A successful compilation provides a high guarantee of correctness.

Rust is safe by default; all memory accesses are checked. It is not possible to corrupt memory by accident.

The unifying principles behind Rust are:

- strictly enforcing safe borrowing of data
- functions, methods and closures to operate on data
- tuples, structs and enums to aggregate data
- pattern matching to select and destructure data
- traits to define behaviour on data

There is a fast-growing ecosystem of available libraries through Cargo to complement the standard library.


## Run without Crash

Code should run without crashing, from the very first time it is run

Rust is a statically typed language and leaves almost no room for errors that would cause a program to crash.

## Fast runtime execution

Rust is extremely fast when it comes to execution time.



Zero-cost abstractions —

Rust code is compiled into Assembly using the LLVM back-end (also used by C).

Programming features like Generics and Collections do not come with runtime cost; it will only be slower to compile. (Source: stackoverflow).


Builds optimized code for Generics

Rust’s compiler can smartly identify the generic code and optimize for each specific type


## Compilation Errors

Rust’s compiler gives excellent feedback in its error messages.

The compiler may offer example code that can be used to resolve an error.


## Documentation

Rust has an amazing documentation and a tutorial guide called The Rust Book.


## Areas of use

- Server-side and other backend applications
- Cloud computing applications, services, and infrastructure
- Distributed systems
- Computer networking
- Computer security
- Embedded development
- Game development
- Web frontends (including WebAssembly)
