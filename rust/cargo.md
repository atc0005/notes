<!-- omit in toc -->
# Cargo

<!-- omit in toc -->
## Table of contents

- [Linting](#linting)
  - [TODO](#todo)
  - [Apply all `clippy` rules one-off](#apply-all-clippy-rules-one-off)
- [Control linting settings via config files](#control-linting-settings-via-config-files)
- [Add dependencies](#add-dependencies)
  - [General](#general)
  - [Add specific version / features](#add-specific-version--features)
- [Multiple Binaries](#multiple-binaries)
- [Installation](#installation)
- [References](#references)

## Linting

### TODO

- Test whether adding the rules to `/home/myuser/.cargo/clippy.toml` or
  `/home/myuser/.clippy/clippy.toml` (not sure which) works

### Apply all `clippy` rules one-off

```shell
cargo clippy --all -- -D warnings
```

## Control linting settings via config files

- `~/.cargo/config.toml`
  - linting rules *can not* be enabled/disabled here

    ```toml
    # /home/myuser/.cargo/config.toml

    # This does not work!
    [lints.rust]
    missing_debug_implementations = "warn"
    ```

- `PROJECT_DIR/Cargo.toml` (e.g., `$HOME/dev/rust-lang-book/Cargo.toml`)
  - linting rules **can** be enabled/disabled here

    ```toml
    # /home/myuser/dev/rust-lang-book/Cargo.toml

    # This works!

    # Rules specific to the compiler.
    [lints.rust]
    missing_debug_implementations = "warn"

    # Rules specific to clippy.
    [lints.clippy]
    enum_glob_use = "deny"
    ```

## Add dependencies

### General

```shell
cargo add rand
```

### Add specific version / features

```shell
cargo add tokio@1.35.0 --features "macros,rt-multi-thread,time"
cargo add reqwest@0.11.22
```

## Multiple Binaries

Cargo supports a `default-run` feature to specify which one to use as the
default when `cargo run` is executed.

Example from the <https://github.com/kyclark/command-line-rust> repo (chapter
10):

```toml
[package]
name = "commr"
version = "0.1.0"
edition = "2021"
default-run = "commr"

[dependencies]
anyhow = "1.0.79"
clap = "4.5.0"

[dev-dependencies]
assert_cmd = "2.0.13"
predicates = "3.0.4"
pretty_assertions = "1.4.0"
rand = "0.8.5"
```

## Installation

```shell
cargo install cargo-clean-recursive
```

## References

- <https://doc.rust-lang.org/cargo/reference/manifest.html#the-lints-section>
- <https://doc.rust-lang.org/rustc/lints/listing/allowed-by-default.html#missing-debug-implementations>
- <https://github.com/rust-lang/rust-clippy>
- <https://stackoverflow.com/questions/51785457/how-can-i-specify-which-crate-cargo-run-runs-by-default-in-the-root-of-a-cargo>
