# GraphQL Mutations

A __mutation__, in @[GraphQL][], is a request that may modify the state of the 
server. Otherwise, they look much like @[queries][].

An example query (on some hypothetical @[schema][graphql-schema]) that sets the
`name` of a particular user, identified by their `id` might look as follows:

```graphql
query SetUserName($id: String!, $name: String!) {
    setUserName(id: $id, name: $name) {
        name
    }
}
```

Though there is technically nothing stopping a regular query from making changes
to the server (it's up to the server to implement such things) the reason mutations
are important is that they have stricter order of execution. While queries may be 
parallelized or reordered as the server sees fit, when multiple mutations are specified
in one request, they are to execute sequentially, and if one fails, the rest are skipped.

Only the top level of the query can be sequentialized in this way, so it is recommended to 
design mutations using a "flat" structure: the top fields of the mutation should define 
individual actions (e.g. `setUserName` as in the example above) and all child fields should 
only be non-mutating queries.
