# Rustup

Rust compiler and tooling manager (install, update, version change)

# Rustc

Rust compiler

```bash
rustc main.rs
```

# Cargo

[Docs](https://doc.rust-lang.org/cargo/)

Rust package manager. 

### Commands

```bash
# build package in development mode
cargo build

# build package in production mode
cargo build --release

# build and execute package
cargo run

# lint code
cargo check

# format package using rustfmt
cargo fmt
```

# Clippy

Better code liner for Rust

### Install

```bash
rustup component add clippy
```

### Commands

```bash
# lint cargo package with clippy
cargo clippy
```

### VSCode Config

_settings.json_
```json 
{
	"rust-analyzer.checkOnSave.command": "clippy"
}
```