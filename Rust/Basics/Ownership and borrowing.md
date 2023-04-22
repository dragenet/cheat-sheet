# Heap

### Ownership
Variables stored in heap behaves like the following:

```rust
    let s1 = String::from("hello");

	// s1 moved to s2, 
	// s1 is invalid beyond this line and cannot be used
    let s2 = s1;

    println!("{}, world!", s2);
    println!("{}, world!", s1); // error
```

```rust
    let s1 = String::from("hello");

	// variables stored in heap can be cloned explicitly
    let s2 = s1.clone();

    println!("s1 = {}, s2 = {}", s1, s2);
```

These rules also applies to functions, [read more](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html#ownership-and-functions).

### Borrowing usign reference

Variables can also be provided using reference. This method allow to avoid moving ownership:

```rust
fn main() {
    let s1 = String::from("hello");

    let len = calculate_length(&s1);

    println!("The length of '{}' is {}.", s1, len);
}

fn calculate_length(s: &String) -> usize {
    s.len()
}
```

#### Mutable References

``` rust
fn main() {
    let mut s = String::from("hello");

    change(&mut s);
}

fn change(some_string: &mut String) {
    some_string.push_str(", world");
}
```

#### Rules of references

-   At any given time, you can have _either_ one mutable reference _or_ any number of immutable references.
-   References must always be valid.

# Stack

Stack-only data implements the `Copy` trait (read more in [docs](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html#stack-only-data-copy))):  
-   All the integer types, such as `u32`.
-   The Boolean type, `bool`, with values `true` and `false`.
-   All the floating-point types, such as `f64`.
-   The character type, `char`.
-   Tuples, if they only contain types that also implement `Copy`. For example, `(i32, i32)` implements `Copy`, but `(i32, String)` does not.