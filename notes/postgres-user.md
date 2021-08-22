# Postgres User

In @[PostgreSQL][] the terms "user" and @[role][database-role] are almost interchangeable. The
only difference is that roles created with the `CREATE USER` commnd, rather than the standard
`CREATE ROLE` are created with log in permission by default. Otherwise, there is no difference.

Attempting to connect to the database using @[`psql`][] will attempt to connect to the database as the
user matching your OS user name (e.g. `whoami`) so it is convenient (and recommended) to [create][]
such a database user in Postgres.

[create]: https://www.postgresql.org/docs/current/sql-createuser.html

The default user is named `postgres`, which may need to be used to create your initial user.
