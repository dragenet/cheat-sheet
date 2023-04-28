[Rust Book](https://doc.rust-lang.org/book/ch06-01-defining-an-enum.html#defining-an-enum)

```rust
enum UsState {
    Alabama,
    Alaska,
}

enum Coin { 
    Penny,
    Nickel,
    Dime,
    Quarter(UsState),
}
```
