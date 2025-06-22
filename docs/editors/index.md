# Editors for Rust




- [Neovim](neovim.md) - Treesitter Rust parser, rusacea.nvim
- [Emacs](emacs.md)
- [VS Code](vscode.md)
- [RustRover](rustrover.md)



## Rust LSP server

Editors with Rust support benefits from the [rust-analyser](), a Language Server Protocol (LSP) implementation for the Rust language.

The rust-analyser server runs a static analysis of the code in a project, returning data about syntax errors and language idioms.

Data is used by LSP clients which are found in the majority of editors (or editor extensions) to display diagnostics in the user interface.
