# Composite Key

A __composite key__ is any @[key][database-key] that is made up of more than one column of a @[relation][database-relation] in a 
@[relational database][]. Often multiple composite keys may exist for a particular piece of 
data, but are irrelevant and not explicitly identified as such.

In a @[join table][], often the keys of the pair of objects being joined forms a composite key,
allowing an unnecessary @[surrogate key][] to be avoided. The use of composite keys is also 
important in avoiding the @[mismatched diamond join][].
