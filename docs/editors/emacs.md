# Emacs

Rust-mode provides core workflow support. [rustic](#rustic-mode)


## Rust-mode
`rust-mode` makes editing [Rust](http://rust-lang.org) code with Emacs enjoyable. It requires Emacs 25 or later, and is included in both [Emacs Prelude](https://github.com/bbatsov/prelude) and [Spacemacs](https://github.com/syl20bnr/spacemacs) by default.

rust-mode provides:

- Syntax highlighting (for Font Lock Mode)
- Indentation
- Integration with Cargo, clippy and rustfmt

This mode does _not_ provide auto completion, or jumping to function / trait definitions.


## rustic mode

Rustic is based on [rust-mode](https://github.com/rust-lang/rust-mode) and provides additional features:

- cargo popup
- multiline error parsing
- translation of ANSI control sequences through
  [xterm-color](https://github.com/atomontage/xterm-color)
- async org babel
- automatic LSP configuration with
  [eglot](https://github.com/joaotavora/eglot) or
  [lsp-mode](https://github.com/emacs-lsp/lsp-mode)
- [eask][] for testing

rustic only shares the rust-mode code from rust-mode.el and rust-utils.el.


## LSP client
