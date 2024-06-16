# Cargo

## Linting

```shell
cargo clippy --all -- -D warnings
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
