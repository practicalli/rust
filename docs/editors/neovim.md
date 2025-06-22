# Neovim for Rust

Neovim provides excellent syntax support via the Treesiter parser for rust.



=== Practicalli Astro

    Provides Rust support via the [Astrocommunity Rust pack](https://github.com/AstroNvim/astrocommunity/tree/main/lua/astrocommunity/pack/rust)

    !!! NOTE "Add Astrocommunity Rust Pack"
        ```lua
          { import = "astrocommunity.pack.rust" },
        ```

    - rust Treesitter parser
    - rustaceanvim for language specific tooling
    - crates.nvim for crate management
    - TOML language support

    `rust-analyzer` shold be added via rustup

    !!! NOTE "Install rust-analyzer via rustup"
        ```shell
        rustup component add rust-analyzer
        ```

        ```shell-output
        ❯ rustup component add rust-analyzer
        info: downloading component 'rust-analyzer'
        info: installing component 'rust-analyzer'
        ```




!!! TIP "rustaceanvim"
    Provides advanced set of tools over the standard Neovim LSP Client that are specific to rust-analyzer
