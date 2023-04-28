[Docs](https://doc.rust-lang.org/book/ch15-05-interior-mutability.html)

The `Rc` smart pointer (short for *reference counting*) is used to share ownership of a value between multiple parts of a Rust program.

> [!warning]
> Single-thread only

## Creating an `Rc` Pointer

To create an `Rc` pointer, use the `Rc::new()` function:

```rust
use std::rc::Rc;

let value = Rc::new(42);
```

This creates an `Rc` pointer that wraps the value `42`. The `Rc` pointer itself is an immutable reference to the value, but it can be cloned to create additional references.

## Cloning an `Rc` Pointer

To clone an `Rc` pointer, use the `clone()` method:

```rust
let value = Rc::new(42);
let reference1 = value.clone();
let reference2 = value.clone();
```

This creates two additional `Rc` pointers that reference the same value as `value`.

## Getting the Strong Count

To get the number of references to the value that an `Rc` pointer is pointing to, use the `strong_count()` function:

```rust
let value = Rc::new(42);
let reference1 = value.clone();
let reference2 = value.clone();
let count = Rc::strong_count(&value); // returns 3
```

## Getting the Weak Count

To get the number of weak references to the value that an `Rc` pointer is pointing to, use the `weak_count()` function:

```rust
use std::rc::Weak;

let value = Rc::new(42);
let weak_reference = Rc::downgrade(&value);
let count = Weak::weak_count(&value); // returns 1
```

Here, we use the `Rc::downgrade()` function to create a `Weak` pointer that references the same value as `value`. The `weak_count()` function returns the number of `Weak` pointers that reference the value.

## Converting an `Rc` Pointer to a Weak Pointer

To convert an `Rc` pointer to a `Weak` pointer, use the `Rc::downgrade()` function:

```rust
let value = Rc::new(42);
let weak_reference = Rc::downgrade(&value);
```

This creates a `Weak` pointer that references the same value as `value`. Note that `Weak` pointers do not count towards the reference count of the value, so the value may be dropped while there are still `Weak` pointers that reference it.

## Upgrading a Weak Pointer to an `Rc` Pointer

To upgrade a `Weak` pointer to an `Rc` pointer, use the `Weak::upgrade()` method:

```rust
let value = Rc::new(42);
let weak_reference = Rc::downgrade(&value);
if let Some(reference) = weak_reference.upgrade() {
    // use the reference
}
```

Here, we check if the `Weak` pointer can be upgraded to an `Rc` pointer using the `upgrade()` method. If it can be upgraded, we use the resulting `Rc` pointer. If it cannot be upgraded, the `if let` block is skipped. Note that `Weak` pointers can be upgraded multiple times as long as the value is still alive.