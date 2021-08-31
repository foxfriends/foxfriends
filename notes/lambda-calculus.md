# Lambda Calculus

The Lambda Calculus is a model of computation that can be used to describe
any algorithm, equivalent to the @[Turing Machine][] model.

In the Lambda Calculus, there are only three rules:
1.  Variable: $x$, representing a value.
2.  Abstraction: $\lambda x.M$, where $M$ is another expression in which the variable $x$ is bound.
3.  Application: $M N$, where $M$ and $N$ are both expressions.

Though admittedly hard to see just based on that how this can be useful, these
pieces can be used to build up representations of more and more complex concepts
until it all starts to make sense.

The Lambda Calculus can be considered to be the basis of all @[functional][functional-programming] 
@[programming languages][programming-language].
