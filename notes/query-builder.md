# Query Builder

A __query builder__ is an application level @[database abstraction][] which allows
the programmer to construct @[SQL][] queries using the syntax of the host
@[programming language][] to simulate the structure of the SQL query.

For example, to construct the query `SELECT name, age FROM users WHERE id = 5`,
the query builder would allow writing something to the effect of
`users.select('name', 'age').where(equals('id', 5))`.
