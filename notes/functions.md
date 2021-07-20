# Functions

A __function__, also sometimes called a *routine* or *subroutine* (typically in more "old fashioned"
situations), is a (usually) named piece of code which can be referred to and executed ("called")
by other code. Functions may receive *arguments* (or *parameters*), and may have a *return value*.
Functions may also be called on a @[receiver][function-receiver], in which case they are typically
referred to as @[methods][].

The calling of functions forms a @[call stack][], enabling control to return to the calling function
at the end of the called function's execution.

In @[functional programming][], functions are typically treated as @[first-class][] values, enabling
great opportunities for code-reuse. Meanwhile with more @[imperative programming][], functions are
often not treated in this way, and cannot be treated as values, only as code.
