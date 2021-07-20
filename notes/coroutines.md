# Coroutines

A (stackful) __coroutine__ is a @[function][functions] which can be suspended and resumed,
similar to a @[generator][generator-function] (or stack*less* coroutine) but providing
more flexibility.

Where the transfer of control between regular functions is done using a single
@[call stack][] on which all function invocations are tracked, a coroutine is
provided its own stack, and the suspending and resuming is performed by switching
between these stacks.

Meanwhile, the generator or stackless coroutine is not given its own stack, and instead
shares the main call stack or uses something else. Though simpler, and often sufficient
in most cases, this does occasionally pose a few limitations.

Note that coroutines are not true @[concurrency][]---there is still only one
@[thread][] involved, so only one instruction executing at any particular time---but
they can be used to similar effect.
