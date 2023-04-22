[Docs](https://doc.rust-lang.org/book/ch07-00-managing-growing-projects-with-packages-crates-and-modules.html#managing-growing-projects-with-packages-crates-and-modules)

# Rust Book Chapter 7: Managing Growing Projects with Packages, Crates, and Modules

## Packages and Crates
A **Package** is a Cargo feature that lets you build, test, and share crates. Packages contain a `Cargo.toml` file that describes how to build those crates. A **Crate** is a tree of modules that produces a library or binary.

## Modules
A **Module** is a namespace that contains definitions of functions or types. A **Path** is a way of naming an item in a module hierarchy.

### Using Modules to Reuse and Organize Code

```rust
// Define a module with the `mod` keyword.
mod sound {
    // Define a function within the module.
    pub fn guitar() {
        // Code for playing guitar...
    }
}

// Bring the module into scope with the `use` keyword.
use crate::sound::guitar;
```

### The Filesystem and Modules

```rust
// File: src/main.rs

// Modules can be defined in separate files.
mod sound;

// Bring the module into scope.
use crate::sound::guitar;

fn main() {
    // Call the function defined in the module.
    guitar();
}
```

### Referring to Names in Different Modules

```rust
// File: src/sound.rs

// Define a module with the `mod` keyword.
mod instrument {
    // Define a function within the module.
    pub fn guitar() {
        // Code for playing guitar...
    }
}

// Bring the module into scope with the `use` keyword.
use self::instrument::guitar;

// Alternatively, you can use a relative path.
use super::instrument::guitar;

fn main() {
    // Call the function defined in the module.
    guitar();
}
```

### Making Structs and Enums Public

```rust
mod sound {
    // Define a public struct.
    pub struct Guitar {
        // Define fields for the struct.
        pub string_count: i32,
        pub fret_count: i32,
    }

    // Define a public enum.
    pub enum Effect {
        Chorus,
        Distortion,
        Phaser,
        Flanger,
    }
}
```

### Re-exporting Names with `pub use
`
```rust
mod sound {
    // Define a function within the module.
    pub fn guitar() {
        // Code for playing guitar...
    }
}

// Re-export the `guitar` function with the `pub use` syntax.
pub use crate::sound::guitar;

fn main() {
    // Call the function using the new path.
    crate::guitar();
}
```

### Using Nested Paths to Clean Up Large `use` Lists

```rust
// A long `use` list can be cleaned up with nested paths.
use std::{cmp::Ordering, io};

fn main() {
    // Call functions from the imported modules.
    let result = cmp::min(5, 10);
    let mut input = String::new();
    io::stdin().read_line(&mut input).unwrap();
}
```
