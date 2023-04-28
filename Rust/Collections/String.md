[Rust Book](https://doc.rust-lang.org/book/ch08-02-strings.html)

Rust's `String` collection is a dynamically resizable, UTF-8 encoded string that is owned by the program.

## Creating a `String`

```rust
let s1 = String::from("hello");
let s2 = "world".to_string();
let s3 = format!("{} {}", s1, s2);
```

A `String` can be created using the `String::from` method, the `to_string` method on a string literal, or the `format!` macro.

## Concatenating `String`s

```rust
let s1 = "hello".to_string();
let s2 = "world".to_string();
let s3 = s1 + &s2;
let s4 = format!("{} {}", s1, s2);
```

`String`s can be concatenated using the `+` operator or the `format!` macro. Note that the `+` operator takes ownership of the left-hand `String`, so a reference to the right-hand `String` must be used.

## Indexing a `String`

```rust
let s = "hello".to_string();
let h = s.chars().nth(0).unwrap();
```

Individual characters of a `String` can be accessed using the `chars` method, which returns an iterator over the characters of the string. The `nth` method can be used to access the nth character of the iterator.

## Slicing a `String`

```rust
let s = "hello".to_string();
let s2 = &s[1..3];
```

A substring of a `String` can be obtained using slicing syntax with a range of indices.

## Modifying a `String`

```rust
let mut s = "hello".to_string();
s.push_str(", world");
s.push('!');
```

A `String` can be modified using the `push_str` and `push` methods to append characters or other strings.

## Converting to/from `String`

```rust
let s1 = "hello".to_string();
let s2 = s1.as_str().to_string();
let s3 = String::from_utf8(vec![104, 101, 108, 108, 111]).unwrap();
```

A `String` can be converted to a string slice using the `as_str` method, and a string slice can be converted to a `String` using the `to_string` method. A `Vec<u8>` of UTF-8 bytes can be converted to a `String` using the `from_utf8` method.