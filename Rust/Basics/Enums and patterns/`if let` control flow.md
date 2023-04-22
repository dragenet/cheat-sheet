The `if let` syntax lets you combine `if` and `let` into a less verbose way to handle values that match one pattern while ignoring the rest.

```rust
// using `match`

let config_max = Some(3u8);
match config_max {
	Some(max) => 
		println!("The maximum is configured to be {}", max),
	_ => (),
}

// same using `if let` syntax

let config_max = Some(3u8);
if let Some(max) = config_max {
	println!("The maximum is configured to be {}", max);
}
```
