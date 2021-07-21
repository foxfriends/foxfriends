# Designing Database Schemas

In my opinion, designing the @[schema][database-schema] well is one of the most important
parts of the process of developing an application which involves a
@[database][relational-database]. If the schema is not good, the application will have trouble
working with that database, and working on the project will just gradually worsen.

When designing a database schema the first goal should be:
1.  to be able to represent any valid state of the application as exactly as possible
2.  without being able to represent any invalid state of the application.

What "valid" and "invalid" mean is somewhat situational, but as a decent rule of thumb,
a "valid" state has a single, meaningful, unambiguous interpretation of what it means,
while an "invalid" state has ambiguous or meaningless interpretation.

For example, in a system representing a simple online shop, there is often no good meaning
for a product that has negative inventory (there is no way to have less than none of
something) or a listing with negative price (nobody pays their buyers to take the
items), so we can prevent those types of situations at the database level. (Of course,
these two examples could still be valid depending on your situation, so do take the time
to consider them fully if you were to design your own shop.)

The next, more concrete, goal of designing the schema is to ensure that it represents
the data without redundancy or duplication. As with any application, but with databases
in particular, having a @[single source of truth][] is critical. One way to ensure that
data exists without redundancy is to strictly follow a @[normal form][database-normal-form],
typically @[BCNF][boyce-codd-normal-form].

The last thing to careful of when designing a database schema is to avoid including
@[business logic][] in the database. The purpose of the database is only to represent
and store valid data, not to be part of your application code. Identifying the divide
between business and data logic is a skill that comes with practice, but in general
it comes down to the same "valid" or "invalid" concept as before: if there is a valid
interpretation of the state (even if it is not a state you expect your application to
be in), it should probably be accepted by the database.

Some of the tricks I use when designing database schemas are:
1.  Use standard, built-in features for as much as possible, avoiding extra
    @[triggers][database-trigger] when unnecessary.
2.  Prefer @[joins][sql-join] over arrays or other multiple-data-in-one-cell type columns.
3.  Avoid @[surrogate keys][surrogate-key] (preferring @[composite keys][composite-key] instead). Use IDs only to
    identify concrete objects.
4.  Use @[enum][enumeration] types (when supported) to restrict strings to a valid set.
5.  Everything should be `NOT NULL` (unless it really must be nullable). Note that in
    database design, `NULL` is a value without meaning. Most often, it should not be
    interpreted as an "unknown value" or "default value".
6.  Prefer to use a unique type such as `UUID` for IDs, rather than an incrementing
    integer.
7.  Do not make sacrifices on the quality of your database for compatibility with the
    database library you are using at the application level. If it is missing support
    for features of the database, it is a bad library anyway.
