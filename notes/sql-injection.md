# SQL Injection

__SQL injection__ is a type of attack used to target applications which make use
of @[SQL][] in an unsafe way, typically by creating queries via string concatenation
with raw user input.

## The attack

Take, for example, this very naïve piece of (@[Javascript][]) code (please never *run*
this example, as it is being used to demonstrate a major @[security][computer-security] flaw).

```javascript
const client = /* some database client */;

const server = /* some hypothetical web server */;
server.post('/login', async (ctx) => {
    const { username, password } = ctx.body;
    const user = await client.query(`SELECT * FROM users WHERE username = '${username}' LIMIT 1`);
    if (compare(user.password, password)) {
        ctx.status(200).end();
    } else {
        ctx.throw(401);
    }
});
```

In this example, we have constructed a SQL query string via regular @[string interpolation][],
inserting the username directly into the query. This is the cause of the vulnerability.

Consider what would happen if someone filled in the login form with the username field set to
`'; drop table users; --'`. With that input, the fully interpolated string becomes:

```sql
SELECT * FROM users WHERE username = ''; drop table users; --' LIMIT 1
```

Notice that this query is now multiple queries, one of them being the very destructive
`drop table users`. And this is hardly the most dangerous thing a user could do! If this
were a banking application, it would be easy to submit
`'; update bankbalance set amount = 100000000000000000000 where userid = {myuserid}; --`
and suddenly have fabricated tons of money.

## The solution

In order to avoid this attack, it is best to simply avoid writing SQL strings directly into
your code. There are plenty of @[database abstractions][] out there that handle dynamically
constructing queries for you in ways that are safe from these attacks.

Of course, there are times when such abstractions will @[leak][law-of-leaky-abstractions]
and writing some custom SQL will become required. In those situations, the next best thing
to refer to the recommendations of the interface you are using. Most provide some way of 
safely defining "replacements", such that you can write the query as 
`SELECT * FROM users WHERE username = $username`, and then you provide the value for
the username and the library will construct the string for you in a way that is safe from
injection (e.g. by using proper @[escaping][string-escaping] techniques).

-----

Finally, no mention of SQL injection is ever complete without a reference to this [xkcx][].

[xkcd]: https://xkcd.com/327/
