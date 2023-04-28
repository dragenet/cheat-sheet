[Rust Book](https://doc.rust-lang.org/book/ch04-00-understanding-ownership.html)

## Ownership

Ownership is Rust's unique way of managing memory. In Rust, every value has a variable that's called its **owner**.

### Rules

1. Each value in Rust has a variable that's called its **owner**.
2. There can only be one owner at a time.
3. When the owner goes out of scope, the value will be dropped.

### Copy Types

Some types like integers and booleans are known as **Copy** types. They are stored on the stack and are cheap to copy, so they are automatically copied when they are assigned to another variable.

### Move Semantics

Other types like Strings and Vectors are known as **Move** types. They are stored on the heap and can be expensive to copy, so when they are assigned to another variable or passed to a function, they are **moved**. This means the original variable will no longer be valid.

## Borrowing

Borrowing is a way to give temporary access to a value to another variable or function, without transferring ownership.

### Rules

1. Multiple references to a value can exist at the same time.
2. References must always be valid.
3. Only one reference can be mutable at a time.

### References

In Rust, a **reference** is a way to refer to a value without taking ownership of it. There are two types of references: **immutable references** and **mutable references**.

Immutable references are created using the `&` operator:

```rust
fn main() {
    let s = String::from("hello");

    let len = calculate_length(&s);

    println!("The length of '{}' is {}.", s, len);
}

fn calculate_length(s: &String) -> usize {
    s.len()
}
```

Mutable references are created using the `&mut` operator:

```rust
fn main() {
    let mut s = String::from("hello");

    change(&mut s);

    println!("The string is now: {}", s);
}

fn change(some_string: &mut String) {
    some_string.push_str(", world");
}
```

### Slices

A **slice** is a reference to a contiguous sequence of elements in a collection. Slices can be mutable or immutable, and are created using the `&[...]` notation.

```rust
fn main() {
    let a = [1, 2, 3, 4, 5];
    let slice = &a[1..3];
    println!("slice = {:?}", slice);
}
```

### Lifetimes

A **lifetime** is a way to express how long a reference should live. Lifetimes are annotated with an apostrophe, and are necessary when working with functions that take references.

```rust
fn main() {
    let string1 = String::from("abcd");
    let string2 = "xyz";

    let result = longest(string1.as_str(), string2);
    println!("The longest string is {}", result);
}

fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}
```

This code uses the `'a` lifetime parameter to specify that the returned reference should have the same lifetime as the shorter of the two input references.

## Summary

- Ownership is Rust's unique way of managing memory.
- Copy types are cheap to copy and are automatically copied when assigned to another variable.
- Move types are expensive to copy and are moved when assigned to another variable or passed to a function.
- Borrowing is