[Docs](https://doc.rust-lang.org/book/ch15-04-rc.html)

Rust provides a number of powerful and flexible iterator types that allow you to perform operations on collections in a concise and expressive manner. Here are some of the most commonly used iterator methods and techniques, along with code examples:

## Creating an Iterator

You can create an iterator by calling the `iter` or `iter_mut` methods on a collection. The `iter` method returns an immutable iterator, while the `iter_mut` method returns a mutable iterator. Here is an example:

```rust
let numbers = vec![1, 2, 3, 4, 5];
let mut iter = numbers.iter();
```

## Basic Iterator Methods

Once you have an iterator, you can use a number of methods to manipulate it. Here are some of the most commonly used ones:

- `next()`: Returns the next element of the iterator. Returns `None` when there are no more elements.
- `filter()`: Filters the elements of the iterator based on a predicate function.
- `map()`: Applies a transformation function to each element of the iterator.
- `fold()`: Accumulates the elements of the iterator into a single value using an accumulator function.

Here are some examples of how to use these methods:

```rust
// filter
let even_numbers = numbers.iter().filter(|n| n % 2 == 0);

// map
let squared_numbers = numbers.iter().map(|n| n * n);

// fold
let sum = numbers.iter().fold(0, |acc, n| acc + n);
```

## Chaining Iterator Methods

You can chain iterator methods together to create complex and expressive data transformations. Here is an example that uses multiple iterator methods to filter, map, and fold a collection of strings:

```rust
let words = vec!["hello", "world", "rust", "iterator"];

let result = words
    .iter()
    .filter(|word| word.len() > 4)
    .map(|word| word.to_uppercase())
    .fold(String::new(), |acc, word| acc + &word);

println!("{}", result); // Output: HELLOWORLDITERATOR
```

## Combinators

Rust also provides a number of higher-order iterator methods that allow you to combine multiple iterators into a single iterator. Here are some of the most commonly used ones:

- `zip()`: Zips two iterators together into a single iterator of tuples.
- `enumerate()`: Returns an iterator of tuples where the first element is the index and the second element is the value.
- `take()`: Returns an iterator that only yields the first n elements of the original iterator.
- `skip()`: Returns an iterator that skips the first n elements of the original iterator.

Here are some examples of how to use these combinator methods:

```rust
let numbers = vec![1, 2, 3, 4, 5];
let letters = vec!['a', 'b', 'c', 'd', 'e'];

// zip
let zipped = numbers.iter().zip(letters.iter());

// enumerate
let enumerated = letters.iter().enumerate();

// take
let first_three = numbers.iter().take(3);

// skip
let last_two = numbers.iter().skip(3);
```

These are some of the most commonly used iterator methods and techniques in Rust. By mastering these techniques, you can write concise and expressive code that is easy to read and maintain.