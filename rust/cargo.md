<!-- omit in toc -->
# Cargo

<!-- omit in toc -->
## Table of contents

- [Linting](#linting)
  - [Apply all `clippy` rules one-off](#apply-all-clippy-rules-one-off)
- [Control linting settings via config files](#control-linting-settings-via-config-files)
- [Add dependencies](#add-dependencies)
  - [General](#general)
  - [Add specific version / features](#add-specific-version--features)
- [Installation](#installation)
- [References](#references)

## Linting

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

## Installation

```shell
cargo install cargo-clean-recursive
```

## References

- <https://doc.rust-lang.org/cargo/reference/manifest.html#the-lints-section>
- <https://doc.rust-lang.org/rustc/lints/listing/allowed-by-default.html#missing-debug-implementations>
- <https://github.com/rust-lang/rust-clippy>
