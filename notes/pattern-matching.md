# Pattern Matching

__Pattern matching__ is a @[programming language][] feature that allows structured
data to be simultaneously compared to an expected shape while also extracting values
from it.

Pattern matching works best when the constructor for the data can be identified
syntactically, as that same constructor syntax is typically to denote the pattern
as well. Languages with @[classes][] with complex constructors tend not to have
pattern matching because the actual shape of the data after a class is constructed
has no relation to the appearance of the constructor call.

Pattern matching becomes particularly useful when working with @[sum types][], as
it provides a simple mechanism by which to write code that branches differently depending
on which constructor was used for that type. As an example, consider the following
@[Rust][] code which uses pattern matching to count the number of leaves in a
@[binary tree][]:

```rust
enum Tree<T> {
    Node(Box<Tree<T>>, Box<Tree<T>>),
    Leaf(T),
}

fn number_of_leaves<T>(tree: &Tree<T>) -> usize {
    match tree {
        Tree::Node(l, r) => number_of_leaves(l) + number_of_leaves(r),
        Tree::Leaf(..) => 1,
    }
}
```

@[Functional programming][] languages tend to support pattern matching, as do other
languages with good support for structured data, such as Rust, seen above, and @[Swift][].

Pattern matching can be extended to be more powerful to the point where it can be
used to write entire programs, as is the case for @[logic programming][] languages
such as @[Prolog][].

@[Destructuring][] is a less powerful but similar concept.

The @[switch statement][] is also somewhat similar to a pattern matching statement, but
again less powerful.
