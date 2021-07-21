# Surrogate Key

In a @[relational database][], a __surrogate key__ is an additional @[primary key][], typically
just an `id`, which is assigned to each row in a @[join table][]. Note that in most join tables, the
relation between the two tables is already unique such that the pair of IDs already forms a
@[composite key][], so the extra surrogate key is not strictly necessary.

Some people prefer to use surrogate keys on all join tables, as the consistent `id` column
on each table can be convenient for quickly identifying individual pieces of data. I,
personally, do not, but really they are not of much harm.
