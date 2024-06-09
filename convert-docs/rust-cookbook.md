# Building Rust Cookbook

## Directions

1. `lxc launch ubuntu:22.04 rust-cookbook`
1. `lxc exec rust-cookbook -- sudo --login --user ubuntu`
1. `sudo apt-get update`
1. `sudo apt-get install -y git build-essential`
1. `curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh`
1. `source $HOME/.cargo/env`
1. `cargo install mdbook mdbook-epub`
1. `git clone https://github.com/rust-lang-nursery/rust-cookbook`
1. `cd rust-cookbook`
1. Modify `book.toml`
    - *see below*
1. `mdbook build`
1. `ls -lh book/epub/`
1. `exit`
1. `lxc file pull rust-cookbook/home/ubuntu/rust-cookbook/book/epub/'Rust Cookbook.epub' ./`

Since I build within an LXD container, the above will generate a new LXD container, build the book and pull the newly generated epub from the container into the host environment.

## Modifications to `book.toml`

`ubuntu@rust-cookbook:~/rust-cookbook$ git diff`

```diff
diff --git a/book.toml b/book.toml
index 8b3bb14..cd25bf4 100644
--- a/book.toml
+++ b/book.toml
@@ -24,3 +24,6 @@ boost-hierarchy = 2
 boost-paragraph = 1
 expand = true
 heading-split-level = 2
+
+[output.epub]
+
```

## Output

```console
...
   Compiling shlex v1.3.0
   Compiling mime v0.3.17
   Compiling webpki-roots v0.25.4
   Compiling pathdiff v0.2.1
   Compiling lazy_static v1.4.0
   Compiling topological-sort v0.2.2
   Compiling base64 v0.21.7
   Compiling mdbook v0.4.36
   Compiling ureq v2.9.1
   Compiling structopt v0.3.26
   Compiling epub-builder v0.7.4
   Compiling html_parser v0.7.0
   Compiling const_format v0.2.32
   Compiling mdbook-epub v0.4.36
    Finished release [optimized] target(s) in 3m 07s
  Installing /home/ubuntu/.cargo/bin/mdbook-epub
   Installed package `mdbook-epub v0.4.36` (executable `mdbook-epub`)
     Summary Successfully installed mdbook, mdbook-epub!
ubuntu@rust-cookbook:~$ git clone https://github.com/rust-lang-nursery/rust-cookbook
Cloning into 'rust-cookbook'...
remote: Enumerating objects: 3825, done.
remote: Counting objects: 100% (152/152), done.
remote: Compressing objects: 100% (73/73), done.
remote: Total 3825 (delta 76), reused 134 (delta 71), pack-reused 3673
Receiving objects: 100% (3825/3825), 2.93 MiB | 5.77 MiB/s, done.
Resolving deltas: 100% (2485/2485), done.
ubuntu@rust-cookbook:~$ cd rust-cookbook
ubuntu@rust-cookbook:~/rust-cookbook$ nano book.toml
ubuntu@rust-cookbook:~/rust-cookbook$ mdbook build
2024-02-02 15:42:47 [INFO] (mdbook::book): Book building has started
2024-02-02 15:42:47 [INFO] (mdbook::book): Running the epub backend
2024-02-02 15:42:47 [INFO] (mdbook::renderer): Invoking the "epub" renderer
Running mdbook-epub as plugin...
2024-02-02 15:43:14 [INFO] (mdbook::book): Running the html backend
```

## References

- <https://github.com/atc0005/notes/issues/74>
- <https://github.com/rust-lang-nursery/rust-cookbook>
