# Promises

A common technique when working with asynchronous programs is to use promises
(also sometimes called futures) to represent values that are "not yet ready".
They are usually used in conjunction with @[`async`/`await`][] syntax to make
the experience feel more "normal".

The [`Promise`][promise], as implemented by @[Javascript][], have a method `.then(cb)`, in
which the callback `cb` is called when the value is "ready" (for whatever
ready means in each situation). The callback is expected to also return a
`Promise`, which will be flattened into the "promise chain", allowing callbacks
to be chained rather than nested as they were in the days of @[Node.js][]
@[callback-hell][].

[promise]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise

A `Promise` can be in any of three states:
1.  Pending: The value is not ready yet
2.  Resolved: The value is ready
3.  Rejected: The task has failed (e.g. an @[exception][] was @[thrown][try-throw-catch])

```javascript
// `fetch()` is a function that returns a `Promise`
const printGoogle = () => fetch('https://google.com')
    .then((response) => {
        // The `Promise` resolves to the response.
        // `response.text()` is also a `Promise`, so return it to
        // add it to the chain.
        return response.text();
    })
    .then((text) => {
        // Chaining off the above, this callback is called when the text 
        // is ready.
        console.log(text);
    })
    .catch((error) => {
        // In the case that the network request fails, the whole `Promise` 
        // chain will reject, and we can catch the error like this.
        console.error(error);
    });
```

The [`Future`][future], as implemented by @[Rust][], works similarly, though mostly through
the [`FutureExt`][future-ext] trait from the [`futures`][futures] crate.

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

More generally, a promise can be considered a @[monad][], where `then` implements `bind`.
