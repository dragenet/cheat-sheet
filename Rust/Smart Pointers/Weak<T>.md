[Docs](https://doc.rust-lang.org/book/ch15-06-reference-cycles.html)

The `Weak<T>` smart pointer is used for creating weak references to `Rc<T>` instances in Rust. A weak reference is a reference that does not contribute to the reference count of an `Rc<T>` instance. This means that the `Rc<T>` instance can be dropped even if weak references to it still exist.

Here are some code examples of how to use `Weak<T>`:

## Creating a Weak reference
```rust
use std::rc::{Rc, Weak};

let rc = Rc::new("hello".to_string());
let weak = Rc::downgrade(&rc);
```

## Upgrading a Weak reference to a Strong reference
```rust
use std::rc::{Rc, Weak};

let rc = Rc::new("hello".to_string());
let weak = Rc::downgrade(&rc);

if let Some(rc2) = weak.upgrade() {
    println!("rc2: {}", rc2);
}
```

## Checking if a Weak reference is still valid
```rust
use std::rc::{Rc, Weak};

let rc = Rc::new("hello".to_string());
let weak = Rc::downgrade(&rc);

if weak.strong_count() > 0 {
    println!("Weak reference is still valid");
} else {
    println!("Weak reference is no longer valid");
}
```

## Conclusion
`Weak<T>` is a useful smart pointer in Rust for creating weak references to `Rc<T>` instances. It allows you to create references that do not contribute to the reference count of an `Rc<T>` instance, which can be useful in situations where you want to avoid circular references.