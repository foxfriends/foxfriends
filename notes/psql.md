# `psql`

The @[command line][] interface for @[PostgreSQL][]. View the [official documentation][] for
more information.

[official documentation]: https://www.postgresql.org/docs/13/app-psql.html

By default, typing `psql` will attempt to connect as a @[user][postgres-user] with the same name
as your operating system user, and to a @[database][postgres-database] with the same name as the user.
Either or both of those may be overridden by passing the relevant arguments:

```sh
psql -U username -d database
```

After successfully connecting to the database, `psql` presents you with a prompt to interactively
run queries.

In addition to running regular @[SQL][] queries, there are a few special commands that can be
used to interact with PostgreSQL itself.

```
\l               # list databases
\c database_name # connect to a different database
\d               # list tables
\d+ table_name   # show more information about a table
\?               # list all the available commands
```
