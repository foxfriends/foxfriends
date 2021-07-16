# Asynchronous Programming

Asynchronous code is any form of code in which the results of a computation are not
available immediately and must be waited for. Rather than @[blocking][] the current
@[thread][] of execution, the goal of asynchronous programming is to pause the
task at hand and allow the same thread to continue working on something else until
the value is ready.

Though it is not quite the same as multi-threading (and in fact, works well with
multi-threading), asynchronous code is a form of parallelism, so similar
considerations must be made as when working with true @[concurrency][].

Common techniques for asynchronous programming include using @[Promises][] to
represent "values not yet ready" and @[`async`/`await`][] to make those promises
look more like synchronous code.
