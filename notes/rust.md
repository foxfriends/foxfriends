# Rust

[Rust][] is one of my favourite @[languages][programming-language] for its powerful
@[type system][], emphasis on safety and speed, and overall great developer experience.

[Rust]: https://rust-lang.org

Though for small enough tasks, the overhead of such a strict @[compiler][] and relatively
large resulting binary size may not be worth dealing with, Rust is great for mid- to
large-size projects where data requirements are no longer something you can keep track
of without assistance.

Rust comes with the @[Cargo][] @[package manager][] for downloading @[crates][rs-crate].
Cargo is also used for building, running, and installing Rust programs.

[crates.io]: https://crates.io

Notable features of Rust include @[ownership][], @[borrowing][], and @[lifetimes][],
enforced by the compiler and not found in nearly any other language, which make
developing @[concurrent][concurrency] programs less prone to error. Though these concepts
contribute to the relatively steep learning-curve of the language, once understood
they are very useful to know how to reason about, even when not developing in Rust.

Despite being fairly low level, Rust remains expressive enough to do pretty much anything
in, featuring many of the other language features you might ask for, and more, including:
*   @[Static typing][]
*   @[Pattern matching][]
*   @[`async`/`await`][rs-async-await]
*   @[Lambdas][]
*   @[Macros][]
