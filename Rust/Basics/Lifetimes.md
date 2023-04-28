[Rust Book](https://doc.rust-lang.org/book/ch10-03-lifetime-syntax.html)

Lifetimes in Rust are used to ensure that references are valid for as long as they are used. They are an important feature of Rust's ownership system.

## Lifetime Annotations

```rust
fn my_function<'a>(arg: &'a str) -> &'a str {
    arg
}
```

Lifetimes are annotated using the `'a` syntax, where `a` is a placeholder for any lifetime name. In this example, the `my_function` function takes a reference to a string with the lifetime `'a` and returns a reference to a string with the same lifetime.

## Lifetime Elision

```rust
fn my_function(arg: &str) -> &str {
    arg
}
```

Rust has a set of rules for eliding (omitting) lifetime annotations in certain cases. In this example, the `my_function` function takes a reference to a string without any explicit lifetime annotation. Rust automatically adds a lifetime annotation to the reference based on the function signature and the lifetime of the arguments.

## Lifetime Parameters

```rust
struct MyStruct<'a> {
    field: &'a str,
}

let my_struct = MyStruct { field: "hello" };
```

Structs and enums can have lifetime parameters, which specify the lifetimes of their fields or variants. In this example, `MyStruct` has a lifetime parameter `'a` that is used to specify the lifetime of its `field` field.

## Lifetime Bounds

```rust
fn my_function<'a, T>(arg: &'a T) -> &'a T
where
    T: 'a,
{
    arg
}
```

Lifetimes can have bounds, which specify that a lifetime must be at least as long as a certain reference or variable. In this example, `my_function` takes a reference to a generic type `T` with the lifetime `'a`, and the lifetime `'a` is bounded by the lifetime of the reference to `T`.

## Static Lifetime

```rust
fn my_function() -> &'static str {
    "hello"
}
```

The `'static` lifetime is a special lifetime that represents the entire duration of the program. References with the `'static` lifetime are valid for the entire lifetime of the program. In this example, `my_function` returns a reference with the `'static` lifetime.