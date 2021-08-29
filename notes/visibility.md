# Visibility

__Visibility__ (or access) describes the ability of code written outside
of a particular scope (@[module][modules], @[package][packages], @[class][], etc.) 
from being able to view or access items (@[variables][], @[types][], @[functions][], etc.) 
declared in that scope.

Levels of visibility found in some @[languages][programming-language] include:
*   Public (any code may access the field)
*   Package level (code in the same @[package][packages] may access the field)
*   Module level (code in the same module may access the field)
*   File level (code in the same file may access the field)
*   Protected (code in the @[class][] and its subclasses may access the field)
*   Private (code only in the same class may access the field)

Of course, which levels are available depend on the semantics of the language
in question - those without classes won't have class-level visibility modifiers,
and those without modules won't have module-level visibility modifiers.

In general, __always opt for the most restrictive visibility__. The less outside
code knows about the internals of a system, the easier it will be to keep
@[coupling][] low.
