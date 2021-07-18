# `async`/`await`

`async` and `await` is a feature of some @[languages][programming-language] that makes
working with @[promises/futures][promises] easier by hiding the calls to `.then()` and
making @[asynchronous code][asynchronous-programming] look like regular (synchronous)
code again.

An "async function" is a @[function][] that returns a promise, and can make use of the
`await` keyword to wait for the value of other promises.

This feature is available in some languages, notably including @[Javascript][js-async-await]
and @[Rust][rs-async-await].

To complete the thought that Promise is a @[monad][], the `async`/`await` syntax
can be similar to the @[`do` notation][monad-do], where `<-` is equivalent to `await`.
As such, the @[generator-to-monad][] transform can be applied to implement async
functions using generators, replacing `.bind()` with `.then()` and `Monad.of`
with `Promise.resolve`.
