# GraphQL Connections

A __connection__ is the recommended way to implement @[pagination][] in a @[GraphQL][]
@[API][application-programming-interface].

To help visualize connections, consider this diagram, which may or may not be 
formatted badly (I'll investigate better diagrams later...):

<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="230px" height="271px" viewBox="-0.5 -0.5 230 271" content="&lt;mxfile host=&quot;app.diagrams.net&quot; modified=&quot;2021-08-12T00:52:55.746Z&quot; agent=&quot;5.0 (X11)&quot; etag=&quot;NkyF0_7UYYU2oueDmXv2&quot; version=&quot;14.9.6&quot; type=&quot;device&quot;&gt;&lt;diagram id=&quot;dxR9QhOYUCUTZRNPvP5Z&quot; name=&quot;Page-1&quot;&gt;7Vldj6IwFP01PjqBFgUfZxz3K9mJidns7L41tEKzlZpSv/bXb5ECFjA4RkTNvphy2t7COffe3toeHC+2nwVaht85JqwHLLztwdceAEPXVb8JsEsBOHRSIBAUp5BdADP6l2jQ0uiKYhIbAyXnTNKlCfo8iogvDQwJwTfmsDln5qpLFJAKMPMRq6I/KZZhinoDq8C/EBqE2cq2pXsWKBusgThEmG8OIDjpwbHgXKatxXZMWMJdxks679OR3vzFBInkKRM89P7Dn/2Kv3rB229C3rfoG+tDbWaN2Ep/sX5bucsoEHwVYZJYsXrwZRNSSWZL5Ce9G6W5wkK5YOrJVs05j6RW0VOP2joRkmyPvreds6G8iPAFkWKnhugJMGNUexDwtAdtCj1Gekh4KEVGPNIuEOSmC5ZUQxP1AdKqnI1T76M8qrCn7ClfJc3MoXiZOvCcbhO2L8Gd7ZrcwcxvD7jzarjz2qIO1rjbkKlVXzBdq2aQNN9UEslgtcpBz22xC0HJM2GV3UENu4O22HUemt1Rx+za4JHprUsN16X3oXOD0zm9XvNOTyL8nNRM6iniUcIcRnG43/ptk7IEnyIpiYj2CLCgQmMp+J+8TgI5kwRXiqxGHk/kSRCGJF2b5uvI0ytMOVULFzI5Q1Mmp8R/zFfCJ3rWYXXVZMguGZJIBERWDO21zD/7fHnBCYVcVd4DRU9VSlncU9K8DaVf3FRHdaW87ZUCtFwunqp8vutnidS9svLVbWmSqFhWX+UyaUqehuuYMy4Kl5hTxkoQYjRIwtxXnkAU/pJkRqrOSM+6Y0ExZscSrXl8EFyifZ0MX/vQauXAAIbgaWBKAkdPEFbyr1N3amgr/4K64uwjAVpL1EXiNTtXN8Yr6DRgS2eZs1M1KFc+oysH7OBeA9a9Vry6oONgHd5/sMJb2l1h+R+Fs3dXeOVgde/eE/47wkUcoXp+uo+s3VqV5ZSytpNlza6yduYRdydR33Fa0sgq76yW27FG1dPKFN2sRi3cZgxGhiDAs08S5IzLDPVY3C6labC4ooOTfw==&lt;/diagram&gt;&lt;/mxfile&gt;"> <defs/><g><rect x="130" y="54" width="90" height="120" fill="#ffffff" stroke="#000000" pointer-events="all"/><ellipse cx="40" cy="160" rx="40" ry="40" fill="#ffffff" stroke="#000000" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 78px; height: 1px; padding-top: 160px; margin-left: 1px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; "><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: #000000; line-height: 1.2; pointer-events: all; white-space: normal; word-wrap: normal; ">Connection</div></div></div></foreignObject><text x="40" y="164" fill="#000000" font-family="Helvetica" font-size="12px" text-anchor="middle">Connection</text></switch></g><ellipse cx="175" cy="25" rx="25" ry="25" fill="#ffffff" stroke="#000000" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 48px; height: 1px; padding-top: 25px; margin-left: 151px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; "><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: #000000; line-height: 1.2; pointer-events: all; white-space: normal; word-wrap: normal; "><div>Node</div></div></div></div></foreignObject><text x="175" y="29" fill="#000000" font-family="Helvetica" font-size="12px" text-anchor="middle">Node</text></switch></g><ellipse cx="175" cy="85" rx="25" ry="25" fill="#ffffff" stroke="#000000" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 48px; height: 1px; padding-top: 85px; margin-left: 151px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; "><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: #000000; line-height: 1.2; pointer-events: all; white-space: normal; word-wrap: normal; "><div>Node</div></div></div></div></foreignObject><text x="175" y="89" fill="#000000" font-family="Helvetica" font-size="12px" text-anchor="middle">Node</text></switch></g><ellipse cx="175" cy="145" rx="25" ry="25" fill="#ffffff" stroke="#000000" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 48px; height: 1px; padding-top: 145px; margin-left: 151px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; "><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: #000000; line-height: 1.2; pointer-events: all; white-space: normal; word-wrap: normal; "><div>Node</div></div></div></div></foreignObject><text x="175" y="149" fill="#000000" font-family="Helvetica" font-size="12px" text-anchor="middle">Node</text></switch></g><ellipse cx="175" cy="245" rx="25" ry="25" fill="#ffffff" stroke="#000000" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 48px; height: 1px; padding-top: 245px; margin-left: 151px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; "><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: #000000; line-height: 1.2; pointer-events: all; white-space: normal; word-wrap: normal; "><div>Node</div></div></div></div></foreignObject><text x="175" y="249" fill="#000000" font-family="Helvetica" font-size="12px" text-anchor="middle">Node</text></switch></g><path d="M 176 210 L 176 180" fill="none" stroke="#000000" stroke-width="2" stroke-miterlimit="10" stroke-dasharray="2 6" pointer-events="stroke"/><path d="M 153.12 97.09 L 74.98 140.6" fill="none" stroke="#000000" stroke-miterlimit="10" pointer-events="stroke"/><rect x="92.5" y="109.33" width="40" height="10" fill="none" stroke="none" transform="rotate(-30,112.5,114.33)" pointer-events="all"/><g transform="translate(-0.5 -0.5)rotate(-30 112.5 114.32999999999993)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 38px; height: 1px; padding-top: 114px; margin-left: 94px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; "><div style="display: inline-block; font-size: 8px; font-family: Helvetica; color: #000000; line-height: 1.2; pointer-events: all; white-space: normal; word-wrap: normal; ">Edge</div></div></div></foreignObject><text x="113" y="117" fill="#000000" font-family="Helvetica" font-size="8px" text-anchor="middle">Edge</text></switch></g><path d="M 79.77 155.7 L 150.15 147.72" fill="none" stroke="#000000" stroke-miterlimit="10" pointer-events="stroke"/><rect x="92.5" y="142" width="40" height="10" fill="none" stroke="none" transform="rotate(-7,112.5,147)" pointer-events="all"/><g transform="translate(-0.5 -0.5)rotate(-7 112.5 147)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 38px; height: 1px; padding-top: 147px; margin-left: 94px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; "><div style="display: inline-block; font-size: 8px; font-family: Helvetica; color: #000000; line-height: 1.2; pointer-events: all; white-space: normal; word-wrap: normal; ">Edge</div></div></div></foreignObject><text x="113" y="149" fill="#000000" font-family="Helvetica" font-size="8px" text-anchor="middle">Edge</text></switch></g><path d="M 73.88 181.26 L 153.84 231.69" fill="none" stroke="#000000" stroke-miterlimit="10" pointer-events="stroke"/><path d="M 68.28 131.72 L 157.32 42.68" fill="none" stroke="#000000" stroke-miterlimit="10" pointer-events="stroke"/><rect x="94.5" y="196" width="40" height="10" fill="none" stroke="none" transform="rotate(30,114.5,201)" pointer-events="all"/><g transform="translate(-0.5 -0.5)rotate(30 114.5 201)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 38px; height: 1px; padding-top: 201px; margin-left: 96px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; "><div style="display: inline-block; font-size: 8px; font-family: Helvetica; color: #000000; line-height: 1.2; pointer-events: all; white-space: normal; word-wrap: normal; ">Edge</div></div></div></foreignObject><text x="115" y="203" fill="#000000" font-family="Helvetica" font-size="8px" text-anchor="middle">Edge</text></switch></g><rect x="90.5" y="77" width="40" height="10" fill="none" stroke="none" transform="rotate(-44,110.5,82)" pointer-events="all"/><g transform="translate(-0.5 -0.5)rotate(-44 110.5 82)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 38px; height: 1px; padding-top: 82px; margin-left: 92px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; "><div style="display: inline-block; font-size: 8px; font-family: Helvetica; color: #000000; line-height: 1.2; pointer-events: all; white-space: normal; word-wrap: normal; ">Edge</div></div></div></foreignObject><text x="111" y="84" fill="#000000" font-family="Helvetica" font-size="8px" text-anchor="middle">Edge</text></switch></g><rect x="189" y="51" width="40" height="20" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 38px; height: 1px; padding-top: 61px; margin-left: 190px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; "><div style="display: inline-block; font-size: 8px; font-family: Helvetica; color: #000000; line-height: 1.2; pointer-events: all; white-space: normal; word-wrap: normal; ">Page</div></div></div></foreignObject><text x="209" y="63" fill="#000000" font-family="Helvetica" font-size="8px" text-anchor="middle">Page</text></switch></g></g></svg>

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
