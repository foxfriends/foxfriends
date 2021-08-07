# Application Programming Interface

An application programming interface, usually just called an __API__, is used to refer
to a number of different types of interface by which two programs (or two parts of one
program) interact.

One of the most important, and sometimes most difficult, parts of programming is defining
good APIs. When an API is well designed, interacting with the system it is acting as the
interface to becomes very easy, often allowing the implementation to be changed completely
without disrupting external code (a sign of low @[coupling][]).

As well as between different modules within a program, the term API is often used to refer
to web APIs allowing separate programs to interact over the Internet. Web APIs typically
follow a well-known architecture built on top of @[HTTP][], such as
@[REST][representational-state-transfer], @[GraphQL][], or @[WebSocket][].
