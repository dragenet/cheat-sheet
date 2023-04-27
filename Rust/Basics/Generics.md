[Docs](https://doc.rust-lang.org/book/ch10-01-syntax.html)

Generics in Rust allow you to write code that can be used with multiple types. They are similar to templates in C++ and Java. Here are some examples of how to use generics in Rust:

## Basic Syntax

```rust
struct MyStruct<T> {
    field: T,
}

fn my_function<T>(arg: T) {
    /* code */
}
```

Generic types are defined using the `<T>` syntax, where `T` is the name of the type parameter. Generic functions are also defined using the `<T>` syntax.

```rust
let my_struct = MyStruct { field: 1 };
let my_string = String::from("hello");
```

Generic types can be used by specifying the type parameter. In this example, `my_struct` is an instance of `MyStruct<i32>` and `my_string` is an instance of `String`.

## Multiple Type Parameters

```rust
struct Pair<T, U> {
    first: T,
    second: U,
}

fn swap_pair<T, U>(pair: Pair<T, U>) -> Pair<U, T> {
    Pair {
        first: pair.second,
        second: pair.first,
    }
}

let pair = Pair { first: 1, second: "hello" };
let swapped_pair = swap_pair(pair);
```

Generic types can have multiple type parameters. In this example, the `Pair` struct has two type parameters `T` and `U`, and the `swap_pair` function swaps the types of the two parameters.

## Trait Bounds

```rust
struct MyStruct<T: Display> {
    field: T,
}

fn my_function<T: Clone + Debug>(arg: T) {
    /* code */
}
```

You can specify trait bounds on type parameters to restrict the types that can be used with a generic type or function. In this example, the `MyStruct` struct can only be used with types that implement the `Display` trait, and the `my_function` function can only be used with types that implement both the `Clone` and `Debug` traits.

## Associated Types

```rust
trait MyTrait {
    type MyType;

    fn my_function(&self) -> Self::MyType;
}

struct MyStruct;

impl MyTrait for MyStruct {
    type MyType = i32;

    fn my_function(&self) -> Self::MyType {
        42
    }
}

let my_struct = MyStruct;
let value = my_struct.my_function();
```

Generic traits can have associated types, which are types that are defined within the trait but are specific to each implementation of the trait. In this example, the `MyTrait` trait has an associated type `MyType`, which is implemented as `i32` for `MyStruct`.
Here You can read more about [[Traits]].

## Where Clauses

```rust
fn my_function<T, U>(arg1: T, arg2: U) -> bool
where
    T: PartialEq,
    U: PartialEq + Clone,
{
    arg1 == arg2.clone()
}

let result = my_function("hello", String::from("hello"));
```

Where clauses can be used to specify trait bounds on multiple type parameters in a more readable way. In this example, the `my_function` function requires that `T` implements `PartialEq` and `U` implements both `PartialEq` and `Clone`.