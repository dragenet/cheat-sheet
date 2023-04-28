[Rust Book](https://doc.rust-lang.org/book/ch11-00-testing.html)

Rust's built-in testing framework allows you to write automated tests for your code. Tests are written in the same Rust file as the code being tested and are run using the `cargo test` command.

## Writing a Test Function

```rust
#[test]
fn test_function_name() {
    // Test code goes here
}
```

To write a test function, annotate the function with the `#[test]` attribute. The test function should have no arguments and return no value.

## Asserting Equality

```rust
assert_eq!(5, add_two(3));
```

The `assert_eq!` macro can be used to assert that two values are equal. If the values are not equal, the test will fail.

## Asserting Inequality

```rust
assert_ne!(3, add_two(3));
```

The `assert_ne!` macro can be used to assert that two values are not equal. If the values are equal, the test will fail.

## Testing for Panics

```rust
#[test]
#[should_panic]
fn test_function_name() {
    // Test code that should panic goes here
}
```

To test for panics, annotate the test function with the `#[should_panic]` attribute. If the test function panics, the test will pass.

## Ignoring a Test

```rust
#[test]
#[ignore]
fn test_function_name() {
    // Test code goes here
}
```

To ignore a test, annotate the test function with the `#[ignore]` attribute. The test will be skipped when running `cargo test`.

## Testing Private Functions

```rust
#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_private_function() {
        assert_eq!(5, private_function(3));
    }
}
```

To test a private function, create a separate test module in the same file as the function being tested. Use the `use` statement to import the private function into the test module.

## Testing a Result

```rust
#[test]
fn test_function_name() -> Result<(), ErrorType> {
    // Test code goes here
}
```

To test a function that returns a `Result`, add the return type to the test function signature. If the `Result` is an `Err`, the test will fail.

## Running Tests

To run tests, use the `cargo test` command in the terminal. This command will run all tests in the current crate. To run tests for a specific module, use the `cargo test module_name` command.