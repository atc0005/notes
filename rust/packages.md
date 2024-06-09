# Rust: Packages

## Multiple crates

Package with four crates (as shown in the `Advanced Rust: Managing Projects`
course on Linked-In Learning):

```console
$ tree my_project/
my_project/
├── Cargo.toml
└── src
    ├── bin
    │   ├── second_bin.rs
    │   └── third_bin
    │       ├── another_module.rs
    │       └── main.rs
    ├── lib.rs
    ├── main.rs
    └── some_module.rs

3 directories, 7 files
```

Breakdown:

1. `my_project/src/main.rs`
   - first binary crate
   - binary crate "root"
1. `my_project/src/some_module.rs`
   - a module within the `my_project` binary crate
1. `my_project/src/lib.rs`
   - first library crate
   - library crate "root"
1. `my_project/src/bin/second_bin.rs`
   - second binary create within the `my_project` package
1. `my_project/src/bin/third_bin/`
   - `main.rs` is the "root" of the `third_bin` binary crate
   - `another_module.rs` is a module within the `third_bin` binary crate

## Building all of the crates within a package

Building all of the crates within the `my_project` package can be done using
one of:

- `cargo build --workspace`
- `cargo build --release --workspace`

## Optional directories

Other optional directories:

- `benches`
- `examples`
- `tests`

```console
$ tree my_project/
my_project/
├── Cargo.toml
├── benches
├── examples
├── src
│   ├── bin
│   │   ├── second_bin.rs
│   │   └── third_bin
│   │       ├── another_module.rs
│   │       └── main.rs
│   ├── lib.rs
│   ├── main.rs
│   └── some_module.rs
└── tests

6 directories, 7 files
```

## References

- <https://doc.rust-lang.org/reference/crates-and-source-files.html>
- <https://doc.rust-lang.org/reference/items/modules.html>
- <https://www.linkedin.com/learning/advanced-rust-managing-projects>
