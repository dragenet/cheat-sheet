[Docs](https://doc.rust-lang.org/book/ch08-03-hash-maps.html)

Rust's `HashMap` type is a collection of key-value pairs that is owned by the program.

## Creating a `HashMap`

```rust
use std::collections::HashMap;

let mut map = HashMap::new();
map.insert("apple", 3);
map.insert("banana", 2);
map.insert("cherry", 5);
```

A `HashMap` can be created using the `new` method and elements can be added using the `insert` method.

## Accessing Elements of a `HashMap`

```rust
use std::collections::HashMap;

let map = [("apple", 3), ("banana", 2), ("cherry", 5)]
    .iter().cloned().collect::<HashMap<_, _>>();
let count_apple = map["apple"];
let count_banana = map.get("banana");
let count_orange = map.get("orange");
let contains_cherry = map.contains_key("cherry");
```

Individual elements of a `HashMap` can be accessed using indexing syntax or the `get` method, which returns an `Option` type that may contain a reference to the value. The `contains_key` method can be used to check if a key exists in the `HashMap`.

## Modifying a `HashMap`

```rust
use std::collections::HashMap;

let mut map = HashMap::new();
map.insert("apple", 3);
map.insert("banana", 2);
map.insert("cherry", 5);

map.insert("apple", 5);
map.remove("banana");
```

A `HashMap` can be modified using the `insert` method to add or update elements, and the `remove` method to remove elements.

## Iterating over a `HashMap`

```rust
use std::collections::HashMap;

let map = [("apple", 3), ("banana", 2), ("cherry", 5)]
    .iter().cloned().collect::<HashMap<_, _>>();

for (key, value) in &map {
    println!("{}: {}", key, value);
}
```

A `HashMap` can be iterated over using a `for` loop with a reference to the `HashMap`.

## Using `HashMap` with Generics

```rust
use std::collections::HashMap;

fn my_function<K, V>(map: HashMap<K, V>) {
    for (key, value) in map {
        println!("{}: {}", key, value);
    }
}
```

`HashMap` can be used with generic key-value types. In this example, `my_function` takes a `HashMap` of any key and value type.

## Updating Elements with `Entry`

```rust
use std::collections::HashMap;

let mut map = HashMap::new();
map.insert("apple", 3);

map.entry("apple").and_modify(|count| *count += 2).or_insert(5);
map.entry("banana").and_modify(|count| *count += 2).or_insert(5);
```

The `entry` method can be used to modify elements in a `HashMap` using a closure. If the key exists, the closure is called with a mutable reference to the value. If the key does not exist, the closure is not called and a new element is inserted using the `or_insert` method.