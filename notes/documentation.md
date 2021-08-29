# Documentation (of code)

Documenting code is an important of writing it. Though the code makes sense to you
now, it likely will not later on when it is not fresh in your mind. That said, poor
documentation can actually [add to the confusion][ripjsb]

[ripjsb]: https://blog.granneman.com/2010/07/31/a-great-example-of-poor-comments-in-your-code/

There are a number of different levels of documentation which are each important in
their own ways.

@[Comments][code-comments] can be inserted directly into the code, typically around
particular lines that will cause confusion. Though the code should strive to be
@[self-documenting][self-documenting code], there are some things which will simply
never be captured by the code itsef, particularly business or design driven decisions,
workarounds put in place for unusual circumstances, notes about hacks or other cut-corners
that should be repaired in future, and so on. Comments simply explaining what a line
of code is doing are rarely useful (any developer can read the code to find that out),
but comments explaining *why* a line of code is doing what it is doing, or why it was
written the way it was are extremely valuable.

Next are comments made to explain how a piece of code is intended to be used. These
comments typically go at the beginning of a @[module][modules] or @[function][functions],
and provide a brief explanation of what the function does, and what its parameters
are used for. Also worth noting here are alternatives that are available for slightly
different situations than the one the function was written for. Without this prompt,
users may not know the alternatives exist and try to misuse the function in question.
The additional benefit of these module/function level comments are that they can be
used to generate external documentation, which typically provides better searching
and stuff for readers of the documentation.

Beyond commenting, another option for in-code documentation is @[literate programming][].
Writing other guides or books manually (outside of the code) is also sometimes a good idea,
particularly if you have built a whole library or come up with a new concept.
