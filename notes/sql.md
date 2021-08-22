# SQL

Short for *structured query language*, SQL is a language used to interact
with (primarily) @[relational databases][relational-database].

It is not a full-powered @[programming language][], so cannot be used for general
purpose programming, but similar concepts apply, particularly those of @[logic programming][].

Instead of writing programs, SQL can only be used for writing *queries* which ask the
database to return a set of data that satisfies the conditions of the query, or to add
or update some of the data stored in the database. Additionally, SQL includes statements
for modifying the @[database schema][], and the access users of different @[roles][database-role] 
have to different parts of the database.

There is an official standard for SQL, which each distinct @[DBMS][database-management-system] 
is expected to implement and support in exactly the same way, making most of the experience of
managing a database the same, regardless of which system is in use. That said, each implementer
may choose to implement extensions or extra features to support specific features of their 
database, or to make things more convenient, so it is important to refer to the documentation
of each individual DBMS when it comes time for use.
