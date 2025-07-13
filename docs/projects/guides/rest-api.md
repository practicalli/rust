# Rest API with Swagger UI

Create an API service that provides a documented and interactive API using Open API.

[Axum]() is the web framework, supported by [Tokio]() async runtime and [Serde]() for JSON serialisation.

??? INFO "Background references"
    [What is a runtime in Rust](https://kerkour.com/rust-async-await-what-is-a-runtime)

    [How to implement an async main function](https://users.rust-lang.org/t/how-to-implement-async-await-in-main/38007)

> NOTE: other web frameworks include [Rocket](), [Warp](), [Actix]()


## Create project

Create a basic project using the Cargo tool.

!!! NOTE ""
    ```shell
    cargo new hello-world --bin
    ```

<!-- TODO: what does the `--bin` flag do ? -->

??? EXAMPLE "Project configuration file"
    ```toml
    [package]
    name = "hello-world"
    version = "0.1.0"
    edition = "2024"

    [dependencies]
    ```


<!-- TODO: use cargo watch for hot reloading on file change -->

## Dependencies


!!! NOTE ""
    Add library dependencies for Axium and other useful libraries
    ```toml title="Cargo.toml"
    [dependencies]
    axum = "0.8"
    tokio = { version = "1.22.0", features = ["full"] }
    serde = { version = "1.0.149", features = ["derive"] }
    ```

<!-- TODO: add swagger ui library dependences later -->


!!! INFO "Updating Crates"
    LSP / Rustaceannvim will automatically detect newer versions of creates available.

    `SPC l a` to select the "Update creates" code action.  Or select "Update all creates" action if there are multiple creates with newer versions.


## Create a web server

Use the Rust standard library to define IP address for the web server and manage errors.

Use axum to define a router and routes to handle requests.


!!! NOTE ""
    Edit the `src/main.rs` and replace the existing code

    ```rust
    use std::{error::Error, net::SocketAddr};

    use axum::{
        routing::get,
        Router,
    };

    #[tokio::main]
    async fn main() -> Result<(), Box<dyn Error>> {
        let addr = SocketAddr::from(([127, 0, 0, 1], 8000));

        let app = Router::new().route("/", get(|| async { "Hello, Axum" }));

        println!("listening on {}", addr);

        axum::Server::bind(&addr)
            .serve(app.into_make_service())
            .await
            .unwrap();

        Ok(())
    }
    ```

## Run and test web server

Start the Rust project in watch mode, so changes are automatically updated on save.

!!! NOTE "Install Bacon"
    ```shell
    cargo install --locked bacon
    ```

> NOTE: bacon has a long list of crate library dependencies... downloading the internet!


!!! NOTE ""
    ```shell
    cargo run
    ```


??? INFO "Bacon is the new cargo watch"
    [Cargo-watch is no longer maintained](https://crates.io/crates/cargo-watch), recommends [bacon](https://dystroy.org/bacon/) the background code checker instead.
