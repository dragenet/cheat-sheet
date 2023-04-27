Sure, here's a cheatsheet about error handling in Rust with code examples in Markdown format:

# Rust Error Handling Cheatsheet

Rust has a robust and expressive error handling system that makes it easy to write reliable and safe code. Rust's error handling is based on the `Result` enum, which represents either success (`Ok`) or failure (`Err`). Here are some examples of how to use Rust's error handling:

## Creating an Error

```rust
fn do_something() -> Result<(), String> {
    // ...
    Err("An error occurred".to_string())
}
```

To create an error, return an `Err` variant of the `Result` enum with an error message. The error message can be any type that implements the `Display` trait.

## Propagating an Error

```rust
fn do_something() -> Result<(), String> {
    // ...
    let result = do_something_else()?;
    // ...
    Ok(())
}
```

To propagate an error, use the `?` operator after calling a function that returns a `Result`. If the function returns an `Err`, the `?` operator will return the error from the current function.

## Matching an Error

```rust
match do_something() {
    Ok(_) => println!("Success"),
    Err(e) => println!("Error: {}", e),
}
```

To match an error, use a `match` statement on the `Result` enum. If the result is `Ok`, the code in the first arm of the `match` will execute. If the result is `Err`, the code in the second arm will execute.

## Chaining Errors

```rust
fn do_something() -> Result<(), Box<dyn Error>> {
    // ...
    let result = do_something_else()?;
    // ...
    Ok(())
}
```

To chain errors, return a `Result` with a type that implements the `Error` trait. This allows you to return any type of error, not just strings.

## Propagating Errors in a Closure

```rust
let result = some_vector.iter().try_for_each(|item| {
    // ...
    do_something(item)?;
    // ...
    Ok(())
});
```

To propagate errors in a closure, use the `?` operator after calling a function that returns a `Result`. If the closure returns an `Err`, the `try_for_each` method will return the error.

## The `?` Operator

```rust
let result = do_something()?;
```

The `?` operator is a shorthand for a match statement. If the result is `Ok`, the value is returned. If the result is `Err`, the error is returned from the current function.

## The `unwrap` Method

```rust
let result = do_something().unwrap();
```

The `unwrap` method returns the value inside an `Ok` variant, or panics if the result is `Err`. Use `unwrap` with caution, as it can lead to unexpected panics.

## The `expect` Method

```rust
let result = do_something().expect("Something went wrong");
```

The `expect` method returns the value inside an `Ok` variant, or panics with a custom error message if the result is `Err`.

## The `map` Method

```rust
let result = do_something().map(|value| value * 2)?;
```

The `map` method applies a function to the value inside an `Ok` variant and returns a new `Result` with the transformed value. If the result is `Err`, the error is propagated. 

## The `unwrap_or` Method

```rust
let result = do_something().unwrap_or(0)
```
