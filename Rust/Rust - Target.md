# Target
The meaning of the term target depends on the context:
- **Cargo Target** — Cargo packages consist of targets which correspond to [[Rust - Artifact|artifacts]] that will be produced. Packages can have library, binary, example, test, and benchmark targets. The list of targets are configured in the `Cargo.toml` [[Rust - Cargo#Cargo.toml - Manifest|manifest]], often inferred automatically by the directory layout of the source files.
- **Target Directory** — Cargo places all built [[Rust - Artifact|artifacts]] and intermediate files in the target directory.
- **Target Architecture** — The OS and machine architecture for the built artifacts are typically referred to as a *target*.
- **Target Triple** — A triple is a specific format for specifying a target architecture. 