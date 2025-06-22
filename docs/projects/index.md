# Projects

Cargo package manager is use to create and work with Rust projects.



## Command reference

| Command | Description |
| --- | --- |
| `cargo new project-name` | Create a new rust project with given name |
| `cargo build` | Build rust project, resolving library dependencies |
| `cargo run` | Run Rust project |
| `cargo test` | Run test runner for Rust project |
| `cargo doc` | Generate Project documentation |
| `cargo publish` | Publish library to crates.io |


 ## Create a new rust project

```shell
cargo new project-name
```

```shell-ouptput
❯ cargo new playground
    Creating binary (application) `playground` package
note: see more `Cargo.toml` keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html
```

Project structure

```shell-output
❯ tree playground
playground
├── Cargo.toml
└── src
    └── main.rs

2 directories, 2 files
```


## Library Dependencies

`Cargo.toml` file in the root of a project is used to define library dependencies for the project.

Define a dependency with its name and version.

```rust
[dependencies]
ferris-says = "0.3.1"
```

`Cargo.lock` contains a log of the specific versions of dependencies for the project, created and updated by the `cargo build` command.


Make the library available with the `use` directive

```rust
use ferris_says::say; // from the previous step
use std::io::{stdout, BufWriter};

fn main() {
    let stdout = stdout();
    let message = String::from("Hello fellow Rustaceans!");
    let width = message.chars().count();

    let mut writer = BufWriter::new(stdout.lock());
    say(&message, width, &mut writer).unwrap();
}
```


`cargo run` will execute the `main` function and return the result (if there is one).
