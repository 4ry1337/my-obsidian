# Cargo
**Cargo** is the [[Rust Programming Language]] [[Packer Manager|package manager]]. It is a tool that allows Rust [[packages]] to declare their various dependencies and ensure repeatable build.

To accomplish this goal, Cargo does four thigs:
1. Introduces two metadata files with various bits of package information.
2. Fetches and builds package's dependencies.
3. Invokes `rustc` or another build tool with the correct parameters to build your package.
4. Introduces conversations to make working with Rust packages easier.

# Dependencies
[crates.to](https://crates.io/) is the Rust community's central package registry that serves as a location to discover and download packages.

To depend on library hosted on crates.io, add it to `Cargo.toml`

## Cargo.toml - Manifest
A [[Manifest|manifest]] is a description of a package or a workspace in a file named `Cargo.toml`

A virtual manifest is a `Cargo.toml` file that only describes a [[Workspace|workspace]], and does not include a package.

## Cargo.lock - Lock file
The **Cargo.lock** lock file is a file that captures the exact version of every dependency used in a workspace or package

## Package Layout
Cargo uses conventions for file placement to make it easy to dive into a new Cargo package.

- `Cargo.toml` and `Cargo.lock` are stored in the package root.
- Source code goes in the `src` directory.
- The default library file is `src/lib.rs`.
- The default executable file is `src/main.rs`.
    - Other executables can be placed in `src/bin/`.
- Benchmarks go in the `benches` directory.
- Examples go in the `examples` directory.
- Integration tests go in the `tests` directory.