[Rust Book](https://doc.rust-lang.org/book/ch03-03-how-functions-work.html#functions)

```rust
fn five(x: usize) -> i32 { 
	x + 5 
}
```

- `->` specifies return type
- expression without semicolon at the end of block is returned implicitly
- early return is also possible using `return` keyword