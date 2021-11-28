# Scripting Language

A __scripting language__ is a type of @[programming language][] that is best suited
to writing @[scripts][].

Scripting languages have a tendency to be higher-level languages with a
@[dynamic type][dynamic-typing] system to make development of such small
simple scripts quick and easy. Also to help reduce the length of the development
cycle, they are usually run by an interpreter, rather than compiled. They tend
not to have a "main" function, as is often found in compiled languages,
and instead receive command line arguments through a global variable.

Despite such languages being most well suited to small scripts, nothing stops people
from using them to write whole applications. Particularly with more general-purpose
scripting languages, such as @[Javascript][], @[Python][] or @[Ruby][], this is quite
common. Though it can be made to work and makes prototyping very easy, because these
languages are less strict, and typically less performant, such an approach does not
scale in the long term (at least, not in my opinion). For larger scale projects, a
more formally structured language may be more sustainable.
