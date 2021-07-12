# Postgres Database

While @[PostgreSQL][] is often referred to as a database, it is actually a
@[DBMS][database-management-system].

Within one installation of @[PostgreSQL][], multiple databases can be created,
each one with a different purpose.

Attempting to connect to the database using @[`psql`][] will attempt to connect to a database
with the same name as the name of the user being connected as, so it is generally convenient
(and recommended) to make [create][] such databases, particularly one matching your OS user name.

[create]: https://www.postgresql.org/docs/current/sql-createdatabase.html

The default database is named `postgres`, corresponding to the default [`postgres` user][].
