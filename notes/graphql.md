# GraphQL

[GraphQL](https://graphql.org/), originally developed by @[Facebook][], is a
method of designing a web @[API][application-programming-interface] that puts
the question of which data to send in the response into the hands of the
requester, rather than the sender (as is usually the case for @[REST][representational-state-transfer] APIs).

GraphQL comes with a language that can be used to both define the schema as well
as to build requests which will be handled by the server. This language is, of
course, not a full @[programming language][] as it can only be used for describing
requests and not for expressing general computations.

In GraphQL, the idea is that the data is represented as a @[graph][]. The
@[schema][graphql-schema] defines the graph, and the requests (@[queries][graphql-query]
or @[mutations][graphql-mutation]) traverse that graph, requesting the individual
pieces of data that are required.

Another of the major advantages of GraphQL over traditional REST APIs is that a
GraphQL endpoint can be introspected, allowing it to be self-documenting and
for clients such as @[GraphiQL][] to provide an interactive interface for
developers to explore the graph and develop queries.
