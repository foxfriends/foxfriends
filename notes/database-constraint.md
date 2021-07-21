# Database Constraint

In a database, it is important to put __constraints__ on attributes so as to restrict the values
that those attributes may contain.

Common types of constraints which are built-in to each @[DBMS][database-management-system] include 
`NOT NULL`, `UNIQUE` and `REFERENCES`, while further constraints based on arbitrary logica can be
implemented using `CHECK` constraints or constraint @[triggers][database-trigger].

When @[designing][designing-database-schemas] a @[database schema][], it is recommended to constrain the data as strictly as 
possible to avoid any case where "invalid" data can be represented by the database.
