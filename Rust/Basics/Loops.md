[Rust Book](https://doc.rust-lang.org/book/ch03-05-control-flow.html#repetition-with-loops)

# `loop` loop

```rust
fn main() {
	let mut counter = 1;
	
	loop {
	    println!("again!");
	
		if counter == 2 {
			break;
		}
	
		counter += 1;
	}
}
```

`loop` loop could alse return using `break` keyword:

```rust
fn main() {
    let mut counter = 0;

    let result = loop {
        counter += 1;

        if counter == 10 {
            break counter * 2;
        }
    };

    println!("The result is {result}");
}
```

# `while` loop

```rust
fn main() {
    let a = [10, 20, 30, 40, 50];
    let mut index = 0;

    while index < 5 {
        println!("the value is: {}", a[index]);

        index += 1;
    }
}
```

# `for` loop

```rust
fn main() {
    let a = [10, 20, 30, 40, 50];

    for element in a {
        println!("the value is: {element}");
    }
}
```

```rust
fn main() {
    for number in (1..4).rev() {
        println!("{number}!");
    }
    println!("LIFTOFF!!!");
}

```