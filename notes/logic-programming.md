# Logic Programming

__Logic programming__ is a @[programming paradigm][] which (sadly) does not get significant
use in the industry when compared to other paradigms. Additionally, where other paradigms are
often mixed-and-matched, logic programming tends to remain on its own.

In logic programming, the program is structured as a collection of *facts* and *rules*,
which are equated using logical reasoning. Through the evaluation of these equations, the
program is executed. What is interesting about logic programming is that it allows for
writing @[non-deterministic][non-determinism] programs, where other paradigms typically do not.

Though it can be used to write whole programs, I find logic programming is more often
used in a @[REPL][] for answering specific questions, or for implementing a particular
small subsection of a larger program, where the non-determinism and ability to write
complex conditions are of value.

One situation where I have used logic programming is in implementing the
[rules for games](https://blog.cameldridge.com/article/20200828-logic-game-scripting/),
in particular, [Root](https://github.com/foxfriends/root) (though not a finished project,
the concept is there).

Examples of logic @[programming languages][programming-language] are @[Prolog][] and
@[Datalog][].
