# Rust Workflow

- Create project
- Open in Editor
- Define dependencies
- build, run, code


## Evaluation

Rust does not provide a REPL however it could be possible to create one.

... is a very basic script that evaluates code agains the Rust Playground API.

> NOTE: Is should be possible to send Rust forms to the compiler and get a result. Perhaps an implementation of nREPL protocol or similar would be valuable?


## Testing


### Nextest

[Nextest](https://github.com/nextest-rs/nextest) is a Next-gen test runner for Rust.

Up to 3 times faster than `cargo test`

- nextest-runner: core logic for cargo-nextest
- nextest-metadata: library for calling cargo-nextest over the command line
- nextest-filtering: parser and evaluator for [filtersets](https://nexte.st/docs/filtersets)
