# Database Abstractions

When working with a @[database][database-management-system] as part of a larger
software application, it is generally not recommended to use @[SQL][] directly
as doing so is prone to such attacks as @[SQL injection][] and can become hard
to maintain as the @[database schema][] changes.

Use of a database abstraction also makes it easier to @[decouple][coupling] the actual
@[DBMS][] that is being used from the application code, as it no longer needs
directly interacts with any implementation specific details of the system, and
instead the abstraction layer does that translation for us.

Different types of common database abstractions are:
*   @[Object-Relational Mapping][]
*   @[Query Builder][]

In @[compiled][compiler] languages, there is also the possiblity of using a
@[language extension][] or @[macro][] to implement compile-time checked SQL,
which is one way to make using raw SQL both safe and resilient to changes in
the database schema.
