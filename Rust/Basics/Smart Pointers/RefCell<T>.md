[Docs](https://doc.rust-lang.org/book/ch15-05-interior-mutability.html)

Rust `RefCell` is a smart pointer that enables you to have multiple, mutable references to a value while enforcing Rust's borrowing rules at runtime. It is commonly used to provide interior mutability in a struct.

> [!warning]
> Single-thread only

## Creating a `RefCell`

```rust
use std::cell::RefCell;

let value = RefCell::new(42);
```

## Borrowing a `RefCell`

```rust
use std::cell::RefCell;

let value = RefCell::new(42);

// Get a mutable reference to the value inside the RefCell
let mut borrowed_value = value.borrow_mut();
```

Note that `borrow_mut()` returns a `RefMut` smart pointer, which enforces Rust's borrowing rules at runtime.

## Modifying the borrowed value

```rust
use std::cell::RefCell;

let value = RefCell::new(42);

let mut borrowed_value = value.borrow_mut();
*borrowed_value = 23;
```

## Borrowing a `RefCell` immutably

```rust
use std::cell::RefCell;

let value = RefCell::new(42);

// Get an immutable reference to the value inside the RefCell
let borrowed_value = value.borrow();
```

## Attempting to borrow mutably when there is an immutable borrow

```rust
use std::cell::RefCell;

let value = RefCell::new(42);

// Borrow the value immutably
let borrowed_value = value.borrow();

// This will panic at runtime because we are attempting to borrow mutably
// when there is an active immutable borrow
let mut borrowed_value_mut = value.borrow_mut();
```

## Clearing a `RefCell`

```rust
use std::cell::RefCell;

let value = RefCell::new(42);

{
    let mut borrowed_value = value.borrow_mut();
    *borrowed_value = 23;
}

value.replace(42);
```

## Converting a `RefCell` into an immutable reference

```rust
use std::cell::RefCell;

let value = RefCell::new(42);

let immutable_reference: &i32 = &*value.borrow();
```

Note that we use the `*` operator to dereference the `RefCell` and get a reference to the value inside. This is necessary because `borrow()` returns a `Ref` smart pointer, not a raw reference.