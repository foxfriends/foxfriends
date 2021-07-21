# Tuple Relational Calculus

The __tuple relational calculus__ is a @[relational calculus][] that deals with whole
*tuples* (rows) of *relations* (tables) in the relational model of a @[relational database][].

>   The following is adapted from my CS348 Piazza post years ago about the relational calculus.
>   Good times.

To understand the relational calculus, consider the following tables and entries in our database.

```
Books
book_id | name           | author   | pub_year
----------------------------------------------
1       | Harry Potter 1 | 1        | 1997
2       | Harry Potter 2 | 1        | 1998
3       | Eragon         | 2        | 2002
4       | Eldest         | 2        | 2005
5       | Hamlet         | 3        | 1603

Authors
author_id | name       | is_dead | birth_year
---------------------------------|-----------
1         | JK Rowling | False   | 1965
2         | Chris      | False   | 1983
3         | Shakespeare| True    | 1564
```

Then, some expressions in the relational calculus and their respective SQL queries are as follows.
It is recommended that you have some familiarity with the @[logical notation][] used for the syntax
of the relational calculus.

-----

$$
\{ \langle N \rangle | \text{Books}\langle \_, N, 1, \_ \rangle \}
$$

```sql
SELECT name FROM Books WHERE author = 1
```

To the left of the `|`, we have the values we want to include in the output of our query.
These values correspond to variables used on the right side of the `|`.

On the right side of the `|`, it says "Books". This means we are asking something
about the books table. In the brackets by books we have 3 kinds of values:
*   An underscore for I don't care about this column (in this case, the `id` and `pub_year`)
*   A variable (e.g. `N`) for I don't specify the value of this column, but we'll call that value `N` (the name).
    When evaluating this query, all values of that field (in this case, each `name`) will, in turn, be assigned
    to `N`.
*   The `1` for this column has to be `1` (in this case, the `author`)


When evaluated, we get the set of all book names where the `author` is `1`

```
name
--------------
Harry Potter 1
Harry Potter 2
```

-----

$$
\{ \langle N \rangle | \exists a.(\text{Authors}\langle \_, N, \_, a\rangle \wedge a > 1950)\}
$$

```sql
SELECT name FROM Authors WHERE birth_year > 1950
```

Now there is the added "exists" thing, which has a variable `a`, and a query in parentheses. Read this as
"There exists a value `a` such that (query)". With this variable `a` introduced, we find the names `N` of
all authors whose `birth_year` is `a`. To restrict `a`, we then require that at the same time, `a > 1950`,
using the and symbol.

```
name
----------
JK Rowling
Chris
```

-----

$$
\{ \langle I, N\rangle | \exists a.(\text{Books}\langle I, N, a, \_ \rangle \wedge \text{Authors}\langle a, \_, True, \_\rangle)\}
$$

```sql
SELECT book_id, b.name FROM Books b INNER JOIN Authors ON author = author_id WHERE is_dead = True
```

The "exists" query can be arbitrarily complex, and the requirements you impose on variables does not have
to be based on a number. This time, we require that at the same time as "the book has author `a`", that
"the author `a` is dead". A @[join][sql-join] is represented by writing the same variable in both tables.

```
book_id | name
----------------
5       | Hamlet
```

-----

$$
\{ \langle N_B, N_A \rangle | \exists a, p, b.( \text{Books}\langle \_, N_B, a, p \rangle \wedge \text{Authors}\langle a, N_A, \_, b \rangle \wedge p > 2000 \wedge b > 1950)\}
$$

```sql
SELECT b.name, a.name FROM Books b INNER JOIN Authors a ON author = author_id WHERE b.pub_year > 2000 AND a.birth_year > 1950
```

Here we have lots of restrictions, so we introduce lots of variables with that exists guy
As before:
*   Where we join tables, we show the same variable in each table
*   Where we have simple restrictions, we just write those restrictions

Result:

```
b.name  | a.name
----------------
Eragon  | Chris
Eldest  | Chris
```

-----

$$
\{ \langle N, P \rangle | \text{Books}\langle \_, N, \_, P \rangle \wedge \neg \exists x.(\text{Books}\langle \_, \_, \_, x\rangle \wedge P > x) \}
$$

```sql
SELECT name, pub_year FROM Books a WHERE NOT EXISTS (SELECT 1 FROM Books b WHERE a.pub_year > b.pub_year)
```

To write that in relational calculus, just translate the `NOT EXISTS` into... not exists!

Note that it is important to be careful that, when writing "not exists" in a relational calculus query,
the resulting non-exists query does not allow values that truly do not exist in the database to appear
in the resulting set. The relational calculus, just being a computational model, does not know anything
about the contents of the tables or the values you expect to exist, so technically you can get
the "infinite set of everything that does not exist in my database" if you were to write the expression
that way.

```
name   | pub_year
-----------------
Hamlet | 1603
```

-----

```sql
SELECT max(birth_year) FROM Author
```

$$
\{ \langle B \rangle | \text{Author} \langle \_, \_, \_, B \rangle \wedge \neg \exists x.(\text{Author}\langle \_, \_, \_, x\rangle \wedge x > B)\}
$$

There is no aggregation in relational calculus, but sometimes you can represent aggregation in another way.
For `MAX`, you could also think of it as "the value for which there are no larger values", and
just translate that statement directly into the relational calculus. Using "not exists" helps for
things like this. "For all" would work as well, but this is left as an exercise to the reader.

```
birth_year
----------
1983
```
