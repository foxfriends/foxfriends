# GraphQL Queries

A __query__, in @[GraphQL][], is a request that only retrieves data (i.e., does not
change, or mutate, the state of the server). Queries are constructed using the
GraphQL query language. Queries may make use of variables which are received as
parameters to allow reusing the same query for many requests.

An example query (on some hypothetical @[schema][graphql-schema]) that gets the
`name` of a particular user, identified by their `id` might look as follows:

```graphql
query GetUsernameById($id: String!) {
    user(id: $id) {
        name
    }
}
```

Multiple queries can be specified in one request, but because queries do not change
the state of the server, the server is free to execute such queries in any order,
or even at the same time. If one fails, the others may complete independently.

For a request that makes changes to the state of the server, it is preferred to use
a @[mutation][graphql-mutation].
