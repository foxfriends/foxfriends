# Mismatched Diamond Joins

One common flaw I have witnessed in many @[database designs][designing-database-schemas]
is that of allowing what I call a *mismatched diamond join*. Take the following
@[schema][database-schema] for example (unnecessary details have been omitted):

```sql
CREATE TABLE shops (
    id INT NOT NULL PRIMARY KEY
);

CREATE TABLE products (
    id INT NOT NULL PRIMARY KEY,
    shop_id INT NOT NULL REFERENCES shops (id)
);

CREATE TABLE locations (
    id INT NOT NULL PRIMARY KEY,
    shop_id INT NOT NULL REFERENCES shops (id)
);

CREATE TABLE inventory (
    product_id INT NOT NULL REFERENCES products (id),
    location_id NOT NULL REFERENCES locations (id),
    quantity INT NOT NULL
);
```

In this situation, it is possible to insert the following:

```sql
-- Create two shops
INSERT INTO shops (id) VALUES (1), (2);
-- Create a product for each shop
INSERT INTO products (id, shop_id) VALUES (1, 1), (2, 2);
-- Create a location for each shop
INSERT INTO locations (id, shop_id) VALUES (1, 1), (2, 2);
-- Now insert inventory for the products
INSERT INTO inventory (product_id, location_id, quantity) VALUES
    (1, 1, 10), -- ok
    (2, 2, 10), -- ok
    (1, 2, 10); -- ok... WAIT: we now have inventory at one location
                --          for a product owned by a different shop!
```

Notice that we product `1` now has inventory in location `2`, but
product `1` is owned by shop `1` while location `2` is owned by shop
`2`, which is not a situation that should occur! Because we did not
include a restriction that the product must be from the same shop
as the location, we are now able to include what I consider to be
(non-business logic) invalid data in our database!

The easy solution in this situation is to include the `shop_id` on
the `inventory` table with the appropriate composite @[foreign key][]
references:

```sql
-- ... the rest is the same

CREATE TABLE inventory (
    product_id INT NOT NULL REFERENCES products (id),
    shop_id INT NOT NULL REFERENCES shops (id),
    location_id INT NOT NULL REFERENCES locations (id),
    quantity INT NOT NULL,
    FOREIGN KEY (location_id, shop_id) REFERENCES locations (id, shop_id),
    FOREIGN KEY (product_id, shop_id) REFERENCES products (id, shop_id)
);
```
