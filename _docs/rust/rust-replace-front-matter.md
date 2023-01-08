---
title: "rust front matter"
excerpt: "Rust, front matter."
last_modified_at: 2021-05-11T10:23:16-04:00
toc: true
---
# Replace Front Matter

Problem:  I have 12 markdown files with a Front Matter attribute I want to change.   The layout is "posts" and I want to change this to "single".

Options:  Linux sed/awk, (sed - stream editor:

```
sed -i 's/old-text/new-text/g' input.txt
sed -i 's/layout: posts/layout: single/g' input.txt
```

Challenge:  Do this in Rust to start learning Rust.  The word "post" is too generic for a global replace.

## Rust String
- [serde](https://serde.rs/) : Serde is a framework for serializing and deserializing Rust data structures efficiently and generically. [serde @ crates.io](https://crates.io/crates/serde), [serde json](https://crates.io/crates/serde_json)
  - [Rust crate serde_frontmatter](https://docs.rs/serde-frontmatter/latest/serde_frontmatter/) : This crate is a Rust library for using the Serde serialization framework with Jekyll-style front matter. `use serde_frontmatter;`

## Logical Steps
- read files by command argument
  - sad (search and replace) - a __sad__ implementation :)
  - sad *.md : prints all files matching [glob](https://man7.org/linux/man-pages/man7/glob.7.html) - see [Rust Cookbook - Directory Traversal](https://rust-lang-nursery.github.io/rust-cookbook/file/dir.html)
- start with one file (avoid the looping)
  - read file [rust read file](https://doc.rust-lang.org/book/ch12-02-reading-a-file.html)
    - parse args : [rust args](https://doc.rust-lang.org/book/ch12-01-accepting-command-line-arguments.html), [gray_matter](https://crates.io/crates/gray_matter)
    - parse out YAML
    - parse out Content
    - with YAML
      - find layout:
      - change attribute to "single"
  - print YAML, deserialized
  - options:
    - https://docs.rs/markdown-parser/0.1.2/markdown_parser/




# Basic Rust

## Serde - Steps
  1. Declare crate dependency for serde. [link](https://doc.rust-lang.org/cargo/reference/specifying-dependencies.html).  Add dependencies to cargo.toml file.
  1. Ensure dependencies enable the serde derive feature [link](https://serde.rs/derive.html)


  # Python
  - [Python Frontmatter](https://pypi.org/project/python-frontmatter/)
