# Javascript: `Promise`

The @[`Promise`][promises], as implemented by @[Javascript][], have a method `.then(cb)`,
in which the callback `cb` is called when the value is "ready" (for whatever
ready means in each situation). The callback is expected to also return a
`Promise`, which will be flattened into the "promise chain", allowing callbacks
to be chained rather than nested as they were in the days of @[Node.js][]
@[callback-hell][].

Since Javascript supports @[`async`/`await`][js-async-await], we can mostly
avoid working with promises directly, but they are still useful to understand.

See the [MDN documentation on Promises][doc] for more information.

[doc]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise

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
