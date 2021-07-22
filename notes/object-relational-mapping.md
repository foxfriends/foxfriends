# Object-Relational Mapping

An __object-relational mapping__ (ORM) is an application-level @[database abstraction][]
typically used in @[object-oriented][object-oriented-programming] @[programming languages][programming-language],
in which the database tables are represented by classes, and the entries in those
tables instances of that class. We map the objects (in the OOP sense) to the relations
(in the @[relational database][] sense).

For example, given the table users with columns `id`, `name`, and `email`, we might create
a class `Users` for it as follows:

```
class User extends ORM.Table {
    id: int;
    name: string;
    email: string;
}
```

The ORM library would typically provide such a base class as the `ORM.Table` described
above, which would then be able to implement @[functions][] such as `User.findById(5)`
which would make the query `SELECT * FROM users WHERE id = 5` and then transform the
result into an instance of the `User` class.

Personally, I am not a fan of ORMs. Though they make a lot of sense for simple
applications, they tend to fall apart when more complex queries need to be constructed,
as is the case in most applications as they grow more and more complex.
