# Compiler

A programming language __compiler__ is a program that converts code written in a
@[programming language][] into a resulting binary format which directly encodes
the machine instructions that make up the program described by the code.

We call languages which have a compiler "compiled languages", as opposed to
@[interpreted languages][interpreter].

The process of compiling, that the compiler performs, is typically performed in a
number of passes over the original source code, incrementally processing and
transforming it until the final output can be computed. Some of those steps are:
1.  @[Lexing][]
2.  @[Parsing][]
3.  Constructing an @[AST][] (or other structured representation of the code)
4.  Weeding and checking
5.  @[Optimizing][optimization]
6.  @[Code generation][]
