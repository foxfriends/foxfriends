# Rust: `async`/`await`

@[Rust][] has support for @[`async`/`await`][]. What is different about Rust's
version is that instead of `await` being a keyword that floats in front of the 
value, `.await` is chained to the end similarly to a method or property.
Arguably, this is the superior syntax, as it allows method chains to contain
awaits within them.

Using the same example as the @[Javascript `async`/`await`][js-async-await] page:

```rust
// Pretend we had fetch in Rust that worked the same as Javascript.
async fn print_google() -> Result<(), _> {
    let text = fetch("https://google.com")
        .await?
        .text()
        .await?;
    println!("{}", text);
}
```
