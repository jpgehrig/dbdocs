This section lists the names of the scripts that create the customer orders (`CO`) schema and describes the objects in the schema.

Table 4-36 lists the `CO` scripts in alphabetical order, while Table 4-37 lists its objects.

Table 4-36 CO Sample Schema Scripts

| Script Name                  | Description                                                   |
|:-----------------------------|:--------------------------------------------------------------|
| `co_ddl.sql`                 | Creates tables, views and indexes                             |
| `co_dml.sql`                 | Populates the tables                                          |
| `co_drop_objects.sql`        | Drops `CO` objects from current schema                        |
| `co_drop_user.sql`           | Drops `CO` user                                               |
| `co_main.sql`                | Main installation script for `CO` schema; calls other scripts |
| `co_set_identity_starts.sql` | Resets the current value of the identity columns              |
| `co_user.sql`                | Creates the `CO` database user                                |
| `customers.sql`              | Inserts for the `customers` table                             |
| `orders.sql`                 | Inserts for the `orders` table                                |
| `order_items.sql`            | Inserts for the `order_items` table                           |
| `products.sql`               | Inserts for the `products` table                              |
| `sample_queries.sql`         | Provides example SQL statements for data analysis             |
| `stores.sql`                 | Inserts for the `stores` table                                |

Table 4-37 CO Sample Schema Objects

| Object Type | Objects                                                                                                                                                                                                                                                                                                                                                                               |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Index       | `customers_name_i`, `orders_customer_id_i`, `orders_store_id_i`, `products_pk`, `stores_pk`, `store_name_u`, `customers_pk`, `customers_email_u`, `store_at_least_one_address_c`,` products_json_c`, `orders_pk`, `orders_customer_id_fk`, `orders_status_c`, `orders_store_id_fk`, `order_items_order_id_fk`, `order_items_product_id_fk`, `order_items_pk`, `order_items_product_u` |
| Table       | `customers`, `stores`, `products`, `orders`, `order_items`                                                                                                                                                                                                                                                                                                                            |
| View        | `customer_order_products`, `store_orders`, `product_reviews`, `product_orders`                                                                                                                                                                                                                                                                                                        |
