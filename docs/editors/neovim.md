# Neovim for Rust

Neovim provides excellent syntax support via the Treesiter parser for rust.

[rust-analyzer](){target=_blank} provides an LSP server that returns diagnostics to the Neovim LSP Client and/or rustaceanvim

[rustaceanvim](https://github.com/mrcjkb/rustaceanvim){target=_blank} provides [extensive features for rust development](https://github.com/mrcjkb/rustaceanvim?tab=readme-ov-file#books-usage--features) and integrates with LSP clients.


=== "Practicalli Astro"

    !!! NOTE "Add Astrocommunity Rust Pack"
        ```lua
          { import = "astrocommunity.pack.rust" },
        ```

    Rust support provided via the [Astrocommunity Rust pack](https://github.com/AstroNvim/astrocommunity/tree/main/lua/astrocommunity/pack/rust)

    - rust Treesitter parser
    - LSP support via rust-analyzer & cargo clippy
    - DAP (debug) via codelldb (mason installl)
    - rustaceanvim for rust specific tooling via rust-analyzer
    - crates.nvim for crate management and completion
    - TOML language support
    - [neotest](https://github.com/nvim-neotest/neotest) is a Neovim framework for test runners, i.e. rustaceanvim.neotest

    `rust-analyzer` shold be added via the `rustup` tool

    !!! NOTE "Install rust-analyzer via rustup"
        ```shell
        rustup component add rust-analyzer
        ```

        ```shell-output
        ❯ rustup component add rust-analyzer
        info: downloading component 'rust-analyzer'
        info: installing component 'rust-analyzer'
        ```
