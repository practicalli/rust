# Install Rust

[rustup]() is the defacto installer and version management tool for Rust.


=== "Rustup Install Script"

    !!! NOTE ""
        ```shell
        curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
        ```

    ??? EXAMPLE "Install output"
        ```shell-output
        ❯ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
        info: downloading installer

        Welcome to Rust!

        This will download and install the official compiler for the Rust
        programming language, and its package manager, Cargo.

        Rustup metadata and toolchains will be installed into the Rustup
        home directory, located at:

          /home/practicalli/.rustup

        This can be modified with the RUSTUP_HOME environment variable.

        The Cargo home directory is located at:

          /home/practicalli/.cargo

        This can be modified with the CARGO_HOME environment variable.

        The cargo, rustc, rustup and other commands will be added to
        Cargo's bin directory, located at:

          /home/practicalli/.cargo/bin

        This path will then be added to your PATH environment variable by
        modifying the profile files located at:

          /home/practicalli/.profile
          /home/practicalli/.bashrc
          /home/practicalli/.config/zsh/.zshenv

        You can uninstall at any time with rustup self uninstall and
        these changes will be reverted.

        Current installation options:


           default host triple: x86_64-unknown-linux-gnu
             default toolchain: stable (default)
                       profile: default
          modify PATH variable: yes

        1) Proceed with standard installation (default - just press enter)
        2) Customize installation
        3) Cancel installation

        info: profile set to 'default'
        info: default host triple is x86_64-unknown-linux-gnu
        info: syncing channel updates for 'stable-x86_64-unknown-linux-gnu'
        info: latest update on 2025-05-15, rust version 1.87.0 (17067e9ac 2025-05-09)
        info: downloading component 'cargo'
        info: downloading component 'clippy'
        info: downloading component 'rust-docs'
         19.9 MiB /  19.9 MiB (100 %)  13.6 MiB/s in  1s
        info: downloading component 'rust-std'
         29.4 MiB /  29.4 MiB (100 %)  15.2 MiB/s in  2s
        info: downloading component 'rustc'
         76.3 MiB /  76.3 MiB (100 %)  14.1 MiB/s in  5s
        info: downloading component 'rustfmt'
        info: installing component 'cargo'
        info: installing component 'clippy'
        info: installing component 'rust-docs'
         19.9 MiB /  19.9 MiB (100 %)   5.9 MiB/s in  2s
        info: installing component 'rust-std'
         29.4 MiB /  29.4 MiB (100 %)   9.4 MiB/s in  3s
        info: installing component 'rustc'
         76.3 MiB /  76.3 MiB (100 %)  10.9 MiB/s in  7s
        info: installing component 'rustfmt'
        info: default toolchain set to 'stable-x86_64-unknown-linux-gnu'

          stable-x86_64-unknown-linux-gnu installed - rustc 1.87.0 (17067e9ac 2025-05-09)


        Rust is installed now. Great!

        To get started you may need to restart your current shell.
        This would reload your PATH environment variable to include
        Cargo's bin directory (/home/practicalli/.rust/cargo/bin).

        To configure your current shell, you need to source
        the corresponding env file under /home/practicalli/.rust/cargo/.

        This is usually done by running one of the following (note the leading DOT):
        . "/home/practicalli/.rust/cargo/env"            # For sh/bash/zsh/ash/dash/pdksh
        source "/home/practicalli/.rust/cargo/env.fish"  # For fish
        source $"/home/practicalli/.rust/cargo/env.nu"   # For nushell
        ```



    ??? EXAMPLE "Custom install locations"
        Set `RUSTUP_HOME` and `CARGO_HOME` environment variables to use a custom location.

        ```config title="~/.zshrc"
        # Rust Lang Development tools
        export RUSTUP_HOME="${RUSTUP_HOME:=$HOME/.config/rust/rustup}"
        export CARGO_HOME="${CARGO_HOME:=$HOME/.config/rust/cargo}"
        ```


        ```shell-output
        ❯ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
        info: downloading installer

        Welcome to Rust!

        This will download and install the official compiler for the Rust
        programming language, and its package manager, Cargo.

        Rustup metadata and toolchains will be installed into the Rustup
        home directory, located at:

          /home/practicalli/.config/rust/rustup/

        This can be modified with the RUSTUP_HOME environment variable.

        The Cargo home directory is located at:

          /home/practicalli/.config/rust/cargo/

        This can be modified with the CARGO_HOME environment variable.

        The cargo, rustc, rustup and other commands will be added to
        Cargo's bin directory, located at:

          /home/practicalli/.config/rust/cargo/bin

        This path will then be added to your PATH environment variable by
        modifying the profile files located at:

          /home/practicalli/.profile
          /home/practicalli/.bashrc
          /home/practicalli/.config/zsh/.zshenv

        You can uninstall at any time with rustup self uninstall and
        these changes will be reverted.

        Current installation options:


           default host triple: x86_64-unknown-linux-gnu
             default toolchain: stable (default)
                       profile: default
          modify PATH variable: yes

        1) Proceed with standard installation (default - just press enter)
        2) Customize installation
        3) Cancel installation


        info: profile set to 'default'
        info: default host triple is x86_64-unknown-linux-gnu
        info: syncing channel updates for 'stable-x86_64-unknown-linux-gnu'
        info: latest update on 2025-05-15, rust version 1.87.0 (17067e9ac 2025-05-09)
        info: downloading component 'cargo'
        info: downloading component 'clippy'
        info: downloading component 'rust-docs'
         19.9 MiB /  19.9 MiB (100 %)  13.6 MiB/s in  1s
        info: downloading component 'rust-std'
         29.4 MiB /  29.4 MiB (100 %)  15.2 MiB/s in  2s
        info: downloading component 'rustc'
         76.3 MiB /  76.3 MiB (100 %)  14.1 MiB/s in  5s
        info: downloading component 'rustfmt'
        info: installing component 'cargo'
        info: installing component 'clippy'
        info: installing component 'rust-docs'
         19.9 MiB /  19.9 MiB (100 %)   5.9 MiB/s in  2s
        info: installing component 'rust-std'
         29.4 MiB /  29.4 MiB (100 %)   9.4 MiB/s in  3s
        info: installing component 'rustc'
         76.3 MiB /  76.3 MiB (100 %)  10.9 MiB/s in  7s
        info: installing component 'rustfmt'
        info: default toolchain set to 'stable-x86_64-unknown-linux-gnu'

          stable-x86_64-unknown-linux-gnu installed - rustc 1.87.0 (17067e9ac 2025-05-09)


        Rust is installed now. Great!

        To get started you may need to restart your current shell.
        This would reload your PATH environment variable to include
        Cargo's bin directory (/home/practicalli/.config/rust/cargo/bin).

        To configure your current shell, you need to source
        the corresponding env file under /home/practicalli/.config/rust/cargo.

        This is usually done by running one of the following (note the leading DOT):
        . "/home/practicalli/.config/rust/cargo/env"            # For sh/bash/zsh/ash/dash/pdksh
        source "/home/practicalli/.config/rust/cargo/env.fish"  # For fish
        source $"/home/practicalli/.config/rust/cargo/env.nu"  # For nushell
        ```


## Confirm Install

`cargo --version` command in a terminal to test Rust and Cargo installed


## Tools

The Rustup script installs several tools


- rust : version 1.87.0 (17067e9ac 2025-05-09)
- rustc :
- rustfmt :
- rust-std :
- rust-docs :
- cargo :
- clippy :


## Update

!!! NOTE ""
    ```shell
    rustup update
    ```




!!! TIP "clangd for faster compilation speed ?"
