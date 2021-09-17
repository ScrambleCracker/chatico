# chatico
Chat server written with Rust and Tokio

### Run
Navigate to directory and run `cargo run`

Then you are able to connect using a `telnet localhost 8080`.
Connect a few clients and type something.

### TIL
`#[tokio::main]` is used to make async functions work w/o adding a boilerplate.

There are different ways to write async code.
`spawn` spawns a task which is executed concurrently
```rust
tokio::spawn(async move {
// async code
});
```

In case you need to execute tasks which are independent and just use some shared state
you can use a macro `tokio::select!`
```rust
tokio::select! {
    result = some_async_fn() => {
        let data = result.unwrap();
        // use result if needed
    }
    _ = other_async_fn() => {
        // or just execute a callback
    }
}
```
