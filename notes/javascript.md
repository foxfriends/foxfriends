# Javascript

Not to be confused with @[Java][], __Javascript__ is a @[scripting language][], originally
created to be used on @[web][web-development] pages but that has grown to become one of
the most widely used @[programming languages][programming-language] for all sorts of
tasks.

In spite of its popularity, Javascript is not really all that great on its own. Due to
its uncontrolled usage on the web, years of... *strange* choices in the design of the
language are forced to stick around and are considered bad practice to use.

Meanwhile, new features are added regularly, but can only be used when the browsers
or engines implement them, as the language itself does not have a "standard" implementation.
Popular implementations include @[Google][]'s @[V8][js-v8] engine and @[Mozilla][]'s
@[SpiderMonkey][]. Useful for checking the availability of features of Javascript that
you want to use are [caniuse.com][] and this [compatibility table][].

[caniuse.com]: https://caniuse.com/
[compatibility table]: https://kangax.github.io/compat-table/es6/

More technically, Javascript is a dialect (or implementation) of the language defined
by @[ECMAScript][] that includes a @[standard library][] suited to web development. As
such, versions of Javascript are often actually referred to by their ECMAScript versions.
Despite this, I will continue to describe language features of Javascript as language
features of Javascript and forget about ECMAScript for the rest of the notes and expect
that, in the case that you want to learn another ECMAScript dialect, you can translate
them yourself.

With that, notable features of *Javascript* include:
*   @[Prototypal inheritance][]
*   @[Dynamic typing][]
*   @[First-class functions][] (including @[lambdas][])
*   Dynamically @[bound][js-bind] @[receivers][function-receiver]
*   @[Destructuring][] (but not full @[pattern matching][])
*   @[Hoisted declarations][declaration-hoisting] (sometimes)
*   @[Promises][js-promises] and @[`async`/`await`][js-async-await] (but not @[concurrency][])
*   @[Generators][js-generator] (but not @[coroutines][])
*   Facilities for @[metaprogramming][] and @[reflection][]
*   A @[module][modules] system (though not always the one used in practice)
*   Inclusion of the @[`Symbol` type][]
