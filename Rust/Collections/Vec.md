[Rust Book](https://doc.rust-lang.org/book/ch08-01-vectors.html)

Rust's `Vec` type is a dynamically resizable array that is owned by the program.

## Creating a `Vec`

```rust
let v1 = vec![1, 2, 3];
let v2: Vec<i32> = Vec::new();
let v3: Vec<i32> = (0..5).collect();
```

A `Vec` can be created using the `vec!` macro, the `new` method, or the `collect` method on an iterator.

## Accessing Elements of a `Vec`

```rust
let v = vec![1, 2, 3];
let first = v[0];
let second = v.get(1);
```

Individual elements of a `Vec` can be accessed using indexing syntax or the `get` method, which returns an `Option` type that may contain a reference to the element.

## Modifying a `Vec`

```rust
let mut v = vec![1, 2, 3];
v.push(4);
v.pop();
v[0] = 5;
```

A `Vec` can be modified using the `push` and `pop` methods to add or remove elements. Elements can be modified using indexing syntax.

## Iterating over a `Vec`

```rust
let v = vec![1, 2, 3];
for element in &v {
    println!("{}", element);
}
```

A `Vec` can be iterated over using a `for` loop with a reference to the `Vec`.

## Using `Vec` with Generics

```rust
fn my_function<T: std::fmt::Display>(v: Vec<T>) {
    for element in v {
        println!("{}", element);
    }
}
```

`Vec` can be used with generic types. In this example, `my_function` takes a `Vec` of any type that implements the `std::fmt::Display` trait.

## Converting to/from Arrays

```rust
let v = vec![1, 2, 3];
let a: [i32; 3] = v.into();
let v2: Vec<i32> = a.into();
```

A `Vec` can be converted to an array using the `into` method. An array can be converted to a `Vec` using the `into` method as well. Note that the length of the array must be specified in the type signature.