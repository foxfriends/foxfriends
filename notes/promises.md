# Promises

A common technique when working with @[asynchronous programs][asynchronous-programming]
is to use promises (also sometimes called futures) to represent values that are "not
yet ready". They are usually used in conjunction with @[`async`/`await`][] syntax to
make the experience feel more "normal".

A `Promise` can be in any of three states:
1.  Pending: The value is not ready yet
2.  Resolved: The value is ready
3.  Rejected: The task has failed (e.g. an @[exception][] was @[thrown][try-throw-catch])

Asynchronous code often comes up when working with @[web][web-development]
technologies, on either @[frontend][frontend-web] or @[backend][backend-web],
so it is no surprise to find promises used heavily in @[Javascript][js-promises].

Many other languages also have implementations of promises (or futures) including
@[Rust][rs-futures]. As promises may be implemented as a library, not all languages
have such first-class support for them as Javascript and Rust.

More generally, a promise can be considered a @[monad][], where `.then()` (or equivalent)
implements `bind` (`>>=`).
