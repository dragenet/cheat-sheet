### Type definition

```rust
let variable: u32 = 10;
```

# Scalar Types

[Docs](https://doc.rust-lang.org/book/ch03-02-data-types.html#scalar-types)

- integers
- floating-point 
- numbers
- Booleans
- characters

# Compound Types

## Tuple

- fixed length
- could group multiple types

```rust
	let tup: (i32, f64, u8) = (500, 6.4, 1);
	let (x, y, z) = tup;
	println!("The value of y is: {y}");
	
	let z = tup.2;
	println!("The value of z is: {z}");
```

## Arrays

- fixed size
- all elements have the same type
- stored on stack

```rust
	let a = [1, 2, 3, 4, 5];
	
	let b: [i32; 5] = [1, 2, 3, 4, 5];
```

# Slice Type

```rust
let s = String::from("hello");

let slice = &s[0..2]; // he
let slice = &s[..2];  // he
let slice = &s[1..];  // ello
let slice = &s[..];   // hello but type is `&str`


```

String literals are slices

```rust
const s = "Hello World" // type of s is &str
```

Slices are also available on other types:

```rust
let a = [1, 2, 3, 4, 5];

let slice = &a[1..3]; // [2,3]

assert_eq!(slice, &[2, 3]);

```

