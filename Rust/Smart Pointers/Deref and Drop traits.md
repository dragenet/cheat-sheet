# Deref Trait

[Rust Book](https://doc.rust-lang.org/book/ch15-02-deref.html)

The `Deref` trait is used to enable the *deref coercion* feature in Rust, which allows a smart pointer to behave like a regular reference by dereferencing it automatically. Here are some examples:

```rust
use std::ops::Deref;

struct MyInt(i32);

impl Deref for MyInt {
    type Target = i32;

    fn deref(&self) -> &Self::Target {
        &self.0
    }
}

let my_int = MyInt(42);
let x: i32 = *my_int;
assert_eq!(x, 42);
```

In this example, `MyInt` is a newtype struct that wraps an `i32`. By implementing the `Deref` trait, we can use the `*` operator on a `MyInt` instance to get the wrapped `i32` value.

# Drop Trait

[Rust Book](https://doc.rust-lang.org/book/ch15-03-drop.html)

The `Drop` trait is used to define the behavior of an object when it goes out of scope. This is often used for resource management, such as closing a file or releasing a lock. Here is an example:

```rust
struct MyResource {
    // ...
}

impl Drop for MyResource {
    fn drop(&mut self) {
        // release the resource
    }
}

{
    let resource = MyResource { /* ... */ };
    // use the resource
} // the resource is automatically released here
```

In this example, we define a new type `MyResource` that implements the `Drop` trait. The `drop` method is called automatically when the `resource` variable goes out of scope. This is where we would release any resources that `MyResource` owns.