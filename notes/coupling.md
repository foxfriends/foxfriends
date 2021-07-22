# Coupling

__Coupling__ in a piece of software refers to the degree to which two separate
parts of the code are dependent on the specifics of the other. "Pieces" in this
case could refer to anything (@[modules][], @[packages][], @[functions][], or
even entirely applications which are interacting with each other).

At all times, the goal of a developer should be to keep coupling *as low as possible*.
This is for a number of reasons:
1.  When two systems are coupled, it becomes hard to change one without changing the other.
2.  When two systems are coupled, and one breaks, the other is likely to break too.
3.  When two systems are coupled, the systems are harder to understand independently of each other.
4.  When two systems are coupled, the code tends to be harder to follow.

Some strategies to help with reducing coupling are:
1.  Include an @[abstraction][] layer between two different components (particularly external libraries).
2.  Define a consistent and well planned public @[API][application-programming-interface] 
    between separate modules.
3.  Avoid passing large numbers of parameters that are used only by nested function calls.
