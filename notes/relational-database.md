# Relational Database

__Relational databases__ represent data as *@[relations][database-relation]* (tables of *attributes*) which
reference each other to describe the relationships between different objects.
Relational databases are implemented by some @[DBMSs][database-management-system].

Most relational databases are interacted with by using @[SQL][]. In theory, it can be 
helpful to think of the relational model using a @[relational calculus][] or 
@[relational algebra][]. In practice, as database are often integrated into a larger
piece of software, application level @[database abstractions][] are used to
hide some of the complexity (and dangers) of using SQL directly.

Personally, if I am in need of a database, I always go to a relational database first.
They are very versatile, and provide great reliability. Only if my particular problem
had truly non-relational data would I think about using another one.
