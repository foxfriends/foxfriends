# Javascript: `async`/`await`

@[Javascript][] supports @[`async`/`await`][] when working with @[promises][].
This is the example from the @[JS Promises][] page transformed to an async function.

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
