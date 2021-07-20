# Generator Function

A __generator__ is a function that can be paused and resumed at specific *yield points*.
This allows the function to generate a sequence of values, but can also be repurposed for
many other interesting applications.

Generators are available in a number of @[languages][programming-language], including
@[Javascript][js-generator] and @[Python][], and also (unstable) @[Rust][].

Some interesting applications of generators:
1.  Implementing @[lazy iteration][lazy-iteration] in typically @[eager][eager-evaluation]
    languages like Javascript.
2.  Implementing @[`async`/`await`][] (or in fact, a @[do-notation][monad-do] for any
    deterministic @[monad][]), using the @[generator-to-monad][] transformation.
3.  Any sort of stateful computation, where a sequence of steps is to be done in a
    specific order.

Also sometimes called "stackless coroutines", generators should not be confused with full
on (stackful) @[coroutines][], which are something else (though similar).
