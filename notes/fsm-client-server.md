# FSM Approach for Stateful Client-Server Interactions

Considering a stateful client-server application, there are often the
following questions that need to be answered:
1.  What is the state of the system (data)?
2.  What actions may be taken right now?
3.  What do those actions do?
4.  How does a user trigger those actions?

To naively build such a system tends to quickly become a big spaghetti
mess. Such a situation I have seen both in my personal projects (board
games ported to web) and at work. We typically end up with something like
1.  Data being checked ad-hoc on both client and server side to determine
    which actions are allowed, leading to large complicated conditions and
    inconsistencies between the two ends.
2.  Long complex functions with lots of duplication to manipulate that data
    for every action that can be taken.
3.  UIs that are hard to build because it's hard to understand what conditions
    make which buttons availble.

One solution I have found to such a situation starts by using a @[finite state machine][].
The FSM makes it possible to declaratively express the *conditions* that make
each action available, and the effects that occur as a result of taking those
actions, as a function of the data. This FSM is placed at the center of the three
pieces (data, server, and client) and acts as the mediator.

```
         Data
          |
Client---FSM---Server
```

The FSM simply needs to implement two interfaces:
1.  Given data (state), output the list of possible actions
2.  Given a description of an action, perform its effects

Now, neither server or client really needs to implement any conditions, they simply
trust the machine to have done it right, as the single source of truth.

The client will call into the machine and receive a list of actions. In a game of
@[Chess][], for example, that list of actions would be a list of all possible moves that
each piece could make.

The client then uses only this list of actions to provide buttons for the player
to click. From the initial state of the board, this would include some list like
`[..., "a2-a3", "a2-a4", "Nb1-a3", "Nb1-c3", ...]`. It is then easy to run through
this list and add buttons to all pieces listed with available moves (here, the pawn
at `a2` and the knight at `b1`). Those buttons would then highlight the squares into
which those pieces could move, and those second buttons send the request back up to
the server.

On the server side, we then expect to receive an action (e.g. `a2-a3`) which can then
be fed directly into the machine to produce the list of actual effects that need to
be performed. Those effects are then easy to implement as independent pieces that do
not need to check any conditions. For example, the effects of the action `a2-a3` could
be simply `movePiece(a2, a3)`. The server does not need to check that the piece was, in
fact, a pawn, or even that the piece existed at all, as all of that logic can be trusted
to the FSM.

The only remaining consideration is the format of those actions. For a game of chess,
this format is pretty obvious, as we already have a well known @[notation][] that can
be used for the purpose.

Another one I have found to work well is using the syntax of a @[logic language][logic-programming]
such as @[Prolog][], as that is a nice succint way to represent rules that can be parsed
and matched against patterns by the client fairly easily.

Of course, nothing says your actions have to be strings at all, they can be any data
format that works for your application.

I would recommend, however, that the server always sends back the *exhaustive* list of
actions, and expects to receive one of those options back *unmodified*. Better not to
rely too heavily on holes in the actions which can be filled, as that starts to
reintroduce questions of what are valid values to use to fill in those blanks. There
are exceptions, of course, such as when receiving arbitrary user input.
