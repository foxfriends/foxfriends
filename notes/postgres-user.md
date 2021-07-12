# Postgres User

@[PostgreSQL][] has a concept of "user" (or "role") that is distinct but related to the users on the
operating system. Understanding this difference tends to make @[setting up][postgres-setup] your
installation of Postgres a lot easier.

Attempting to connect to the database using @[`psql`][] will attempt to connect to the database as the
user matching your OS user name (e.g. `whoami`) so it is convenient (and recommended) to [create][]
such a database user in Postgres.

[create]: https://www.postgresql.org/docs/current/sql-createuser.html

The default user is named `postgres`, which may need to be used to create your initial user.
