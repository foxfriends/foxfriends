# Monads

The __monad__ is a very @[abstract][abstraction] concept which can be used to describe many
different types of computations. Due to the abstractness of the monad, I find that it is
hard to visualize them in any useful way, and to understand the monad fully requires simply
getting a feel for them in a general sense.

Despite this difficulty in locating the concreteness to the monad itself, finding particular
instances of monads is quite easy. In fact, many common data structures and concepts can be
described monadically, for example:
*   The @[option type][]
*   The @[result type][]
*   Contextual information via the @[state monad][]
*   Nondeterminism via the @[list monad][lists]
*   Side effects via the @[IO monad][]
*   @[Promises][]
*   @[Observables][]

More generically, I think of a monad as a way to represent a *compuation as a value* (such
that that "monadic value" can be *evaluated* to produce the regular value). Each type of
monad, as listed above, defines the rules under which that computation operates when being
evaluated.

For the rigid definition of the monad, see the @[monad laws][].

Though @[Haskell][] is the only @[programming language][] I know of to get you to think of
the monad as a concept on its own, the concepts are available and incredibly useful in pretty
much every language you may choose to use. While defining the monad type generically is not
possible without some form of @[higher-kinded types][], individual instances can be implemented
without trouble.

In my own exploration, I have found (deterministic) monads to translate fairly well into
@[Javascript][] using the @[generator to monad][] transformation (being
@[dynamically typed][dynamic-typing], the requirement of higher-kindedness is not an issue).
