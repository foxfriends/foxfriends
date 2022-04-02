# Finite State Machine

A __finite state machine__ (FSM) is a way of representing a system (machine)
that can be in one of a finite number of states. From each state, the machine
may choose from a finite number of actions to reach another state.

Such machines have a number of practical uses. In particular, I have used them
for structuring @[stateful client-server][fsm-client-server] interactions.

More formally a finite state machine can be a @[DFA][deterministic-finite-automaton]
or an @[NFA][nondeterministic-finite-automaton].
