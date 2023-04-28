[Rust Book](https://doc.rust-lang.org/book/ch10-02-traits.html)

Traits in Rust are similar to interfaces in other programming languages. They allow you to define a set of methods that a type must implement.

## Defining a Trait

```rust
trait MyTrait {
    fn my_method(&self);
}
```

Traits are defined using the `trait` keyword, followed by the name of the trait and a set of method signatures. In this example, `MyTrait` defines a single method `my_method`.

## Implementing a Trait

```rust
struct MyStruct;

impl MyTrait for MyStruct {
    fn my_method(&self) {
        /* implementation */
    }
}

let my_struct = MyStruct;
my_struct.my_method();
```

Traits are implemented using the `impl` keyword, followed by the name of the trait and the implementation of each method. In this example, `MyStruct` implements `MyTrait` by providing an implementation for the `my_method` method.

## Default Implementations

```rust
trait MyTrait {
    fn my_method(&self) {
        /* default implementation */
    }
}

struct MyStruct;

impl MyTrait for MyStruct {}

let my_struct = MyStruct;
my_struct.my_method();
```

Traits can provide default implementations for methods. Types that implement the trait can choose to override these implementations or use the default implementation. In this example, `MyTrait` provides a default implementation for `my_method`, and `MyStruct` uses the default implementation.

## Associated Types

```rust
trait MyTrait {
    type MyType;

    fn my_method(&self) -> Self::MyType;
}

struct MyStruct;

impl MyTrait for MyStruct {
    type MyType = i32;

    fn my_method(&self) -> Self::MyType {
        42
    }
}

let my_struct = MyStruct;
let value = my_struct.my_method();
```

Traits can define associated types, which are types that are specific to each implementation of the trait. Types that implement the trait must provide a concrete type for the associated type. In this example, `MyTrait` defines an associated type `MyType` and `MyStruct` provides an implementation for `MyType`.

## Trait Bounds

```rust
fn my_function<T: MyTrait>(arg: T) {
    /* code */
}

struct MyStruct;

impl MyTrait for MyStruct {
    fn my_method(&self) {
        /* implementation */
    }
}

let my_struct = MyStruct;
my_function(my_struct);
```

Functions and structs can have trait bounds, which specify that a type parameter must implement a certain trait. In this example, `my_function` requires that its argument implements `MyTrait`, and `MyStruct` implements `MyTrait`.

## Multiple Trait Bounds

```rust
fn my_function<T: MyTrait + Clone>(arg: T) {
    /* code */
}

struct MyStruct;

impl MyTrait for MyStruct {
    fn my_method(&self) {
        /* implementation */
    }
}

let my_struct = MyStruct;
my_function(my_struct.clone());
```

Multiple trait bounds can be specified using the `+` operator. In this example, `my_function` requires that its argument implements both `MyTrait` and `Clone`.