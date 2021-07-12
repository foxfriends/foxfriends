# Postgres Setup

Create a @[user][postgres-user] and @[database][postgres-database] that matches your system user.

```sh
createuser -slP $(whoami)
createdb $(whoami)
```

Alternatively, within the @[`psql`][] prompt, create users using @[SQL][]:

```sql
CREATE USER "?" WITH SUPERUSER LOGIN PASSWORD '?';
CREATE DATABASE "?";
```
