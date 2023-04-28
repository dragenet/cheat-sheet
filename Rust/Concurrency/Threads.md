[Rust Book](https://doc.rust-lang.org/book/ch16-00-concurrency.html)

Rust provides support for creating threads through the `std::thread` module. Threads allow for parallel execution of code, and Rust's type system ensures that threads are both safe and efficient.

## Creating a Thread

To create a new thread, call the `std::thread::spawn()` function, passing in a closure that contains the code to be executed in the new thread. The closure must have a `move` keyword before its argument to indicate that it takes ownership of any captured variables. 

```rust
use std::thread;

let handle = thread::spawn(move || {
    // thread code here
});
```

The `spawn()` function returns a `JoinHandle` that can be used to wait for the thread to finish execution or to retrieve its return value.

## Waiting for a Thread to Finish

To wait for a thread to finish execution, call the `join()` method on the `JoinHandle` returned by `spawn()`. This method blocks the current thread until the target thread completes its execution.

```rust
let handle = thread::spawn(|| {
    // thread code here
});

handle.join().unwrap(); // blocks until thread finishes
```

The `join()` method returns a `Result` that contains the return value of the thread's closure, if any.

## Sending Data between Threads

To send data from one thread to another, Rust provides the `std::sync::mpsc` module, which stands for *multiple producer, single consumer*. This module provides a channel through which one thread can send messages to another thread.

```rust
use std::sync::mpsc;

let (sender, receiver) = mpsc::channel();

let handle = thread::spawn(move || {
    let message = receiver.recv().unwrap();
    // process message
});

let data = "some data".to_string();
sender.send(data).unwrap();
```

The `mpsc::channel()` function returns two values: a `Sender` and a `Receiver`. The `Sender` can be used to send messages, while the `Receiver` can be used to receive messages.

## Using Mutexes

To allow multiple threads to access a shared resource in a safe and synchronized way, Rust provides the `std::sync::Mutex` type, which stands for *mutual exclusion*. A mutex ensures that only one thread at a time can access the shared resource.

```rust
use std::sync::Mutex;

let mutex = Mutex::new(0);

let handle = thread::spawn(move || {
    let mut data = mutex.lock().unwrap();
    *data += 1;
});

handle.join().unwrap();
let data = mutex.lock().unwrap();
println!("Data: {}", *data); // prints "Data: 1"
```

The `Mutex` type provides the `lock()` method, which returns a `Result` containing a `MutexGuard`. The `MutexGuard` is a smart pointer that grants exclusive access to the shared resource while it is in scope. The `*` operator is used to dereference the `MutexGuard` and access the underlying value.

## Conclusion

Rust's support for threads and synchronization provides a powerful and safe way to write concurrent programs. By using the `std::thread`, `std::sync::mpsc`, and `std::sync::Mutex` modules, Rust programs can take full advantage of modern hardware architectures while avoiding common concurrency pitfalls.