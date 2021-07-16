# `async`/`await`

`async` and `await` is a feature of some languages that makes working with
@[promises/futures][promises] easier by hiding the calls to `.then()` and making the code
look like regular synchronous code again.

An "async function" is one that returns a promise, and can make use of the
`await` keyword to wait for the value of other promises.

Here is the same @[Javascript][] example as on the note for promises but transformed
to an async function:

```javascript
async function printGoogle() {
    try {
        // `fetch()` is a function that returns a `Promise` that resolves to
        // the response. Use `await` to wait for the promise to resolve and
            // just get the value.
        const response = await fetch('https://google.com');
        // `response.text()` is also a `Promise`, so await that too.
        const text = await response.text();
        // Then, when the text is ready, we can print it.
        console.log(text);
    } catch (error) {
        // In the case that the network request fails, the error will be
        // thrown from the `await` for which the promise was rejected.
        console.error(error);
    }
}
```

In @[Rust][] this works similarly, but instead of `await` being a keyword that
floats in front of the future, `.await` is chained to the end of the future.
Arguably, this is the superior syntax, as it allows method chains to contain
awaits within them.

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

To complete the thought that Promise is a @[monad][], the `async`/`await` syntax
can be similar to the @[do][monad-do] syntax, where `<-` is equivalent to `await`.
As such, the @[generator][]-to-monad transform can be applied to implement async
functions using generators and promises as follows:

```javascript
function async_(generator, that, ...args) {
    const next = (iter, input) => {
        const { value, done } = iter.next(input);
        if (done) { return value; }
        return value.then((output) => next(iter, output));
    };
    return next(generator.call(that, ...args));
}
```
