# GraphQL Connections

A __connection__ is the recommended way to implement @[pagination][] in a @[GraphQL][]
@[API][application-programming-interface].

I don't particularly like the way they are named or described (maybe I just
misunderstand their meaning), but here's how it goes anyway.

Start with the actual thing you intend to paginate. This is just a regular model,
containing whatever data is necessary. From here on, we refer to this thing as
the __node__.

```graphql
type Thing {
    id: Id!
    # whatever you want in here
}
```

Connecting those nodes (to the connection) are __edges__, which contain a reference
to the node itself, as well as some information about how to locate that node, such
as the cursor value for this element of the pagination.

> I have also seen the edge also contain `nextNode` and `prevNode`, but I think that
> is just an extension?

```graphql
type ThingEdge {
    node: Thing!
    cursor: String!
}
```

Finally, the __connection__ itself contains the edges as well as some information about the
whole connection and the pagination state.

> The connection may also include other things, like a list of nodes for direct access without
> having to go through edges, but again that is probably just an extension?

```graphql
type ThingConnection {
    totalCount: Int!
    pageInfo: PageInfo!
    edges: [ThingEdge]!
    nodes: [Thing]!
}
```

The __page info__ contains information about the page that is currently being
viewed. This data is specific to your particular implementation of pagination, but should
include enough data that the client is able to understand how many pages there are, what
cursors to use next, and so on.

```graphql
type PageInfo {
    total: Int!
    hasNextPage: Boolean!
    hasPrevPage: Boolean!
    endCursor: String!
    startCursor: String!
}
```

Lastly, to tie it all together, these things are put into the query object somewhere,
typically on a pluralized property, or a property named like  `__Connection`. This
field takes parameters allowing the client to specify which page to load, how many
items, and so on. This is where additional search parameters would be added as well.

```graphql
type Query {
    things(before: String, after: String, limit: Int): ThingConnection!
}

schema {
    query: Query!
}
```

The resulting @[query][graphql-query] then would look something like this:

```graphql
query GetThings($after: String) {
    things(after: $after) {
        pageInfo {
            endCursor
            hasNextPage
        }
        edges {
            node { id }
        }
    }
}
```
