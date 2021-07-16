# Rust: `Future`

The [`Future`][future], as implemented by @[Rust][], is a form of @[promise][promises].
Most features are implemented by the [`FutureExt`][future-ext] trait from the
[`futures`][futures] @[crate][rs-crate].

To reuse the same example from the page on @[Javascript Promises][js-promises], pretend that
`fetch` is a function that exists in Rust.

```rust
use futures::future::err;

// Pretend we had fetch in Rust that worked the same as Javascript.
fn print_google() -> Future<Output = Result<(), _>> {
    fetch("https://google.com")
        .then(|response| response
            .map(|res| res.text())
            .unwrap_or_else(err))
        .then(|text| match text {
            Ok(text) => println!("{}", text),
            Err(error) => eprintln!("{}", error),
        })
}
```

[future]: https://doc.rust-lang.org/std/future/trait.Future.html
[future-ext]: https://docs.rs/futures/0.3.15/futures/future/trait.FutureExt.html
[futures]: https://docs.rs/futures/0.3.15/futures/index.html
