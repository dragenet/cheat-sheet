[Rust Book](https://doc.rust-lang.org/book/ch13-01-closures.html)

Closures are a type of anonymous function that can capture values from their surrounding environment. In Rust, closures are implemented using traits, which define the behavior of the closure. Here are some examples of how to use closures in Rust:

## Basic Syntax

```rust
let closure_name = |parameters| { /* code */ };
```

A closure is defined using the `|parameters|` syntax, where `parameters` are the values that the closure will capture from its surrounding environment. The closure body is defined inside the curly braces `{}`.

```rust
let add = |x, y| x + y;
println!("{}", add(1, 2)); // prints "3"
```

This example defines a closure named `add` that takes two parameters `x` and `y`, and returns their sum.

## Capturing Values

```rust
let x = 1;
let print_x = || println!("{}", x);
print_x(); // prints "1"
```

Closures can capture values from their surrounding environment by reference, mutable reference or by value. In this example, the closure `print_x` captures the value of `x` by reference and prints it.

```rust
let mut x = 1;
let increment_x = || x += 1;
increment_x();
println!("{}", x); // prints "2"
```

In this example, the closure `increment_x` captures the value of `x` by mutable reference, which allows it to modify the value of `x`.

```rust
let x = vec![1, 2, 3];
let print_vec = || println!("{:?}", x);
print_vec(); // prints "[1, 2, 3]"
```

Closures can also capture values by value. In this example, the closure `print_vec` captures the vector `x` by value and prints it.

## Moving Values

```rust
let x = vec![1, 2, 3];
let print_vec = move || println!("{:?}", x);
print_vec(); // prints "[1, 2, 3]"
println!("{:?}", x); // error: use of moved value: `x`
```

When a closure captures a value by value, ownership of the value is transferred to the closure. This is known as a "move" closure. In this example, the closure `print_vec` moves the vector `x` into the closure, so it cannot be used afterwards.

## Returning Closures

```rust
fn create_adder(x: i32) -> impl Fn(i32) -> i32 {
    move |y| x + y
}

let add5 = create_adder(5);
println!("{}", add5(2)); // prints "7"
```

Closures can be returned from functions, but their type cannot be explicitly written. Instead, you can use the `impl Fn` syntax to indicate that the function returns a closure.

In this example, the `create_adder` function takes an integer `x` and returns a closure that takes an integer `y` and returns their sum. The closure captures the value of `x` using a move closure.

## Iterators

```rust
let vec = vec![1, 2, 3, 4, 5];
let sum = vec.iter().fold(0, |acc, x| acc + x);
println!("{}", sum); // prints "15"
```

Closures are commonly used with iterators in Rust. In this example, the `iter()` method is called on a vector to create an iterator, and the `fold()` method is called on the iterator to sum