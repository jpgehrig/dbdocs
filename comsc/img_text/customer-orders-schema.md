This figure shows the relational tables in schema CO and the columns in each table, as well as dependencies between the tables.

The table `products` has the following attributes:

- Columns: `product_id` (primary key), `product_name`,` unit_price`, `product_details`, `product_image`,` image_mime_type`, `image_charset`, `image_filename`,` image_last_updated`.
- Relationships:
  - Column `product_id` relates each row of the table `products` to none or more rows of `product_id` in the `order_items` table.

The `customers` table has the following attributes:

- Columns: `customer_id` (primary key), `email_address`, `full_name`
- Relationships:
  - Column `customer_id` relates each row of the table `customers` to none or more rows of `customer_id` in the `orders` table.

The `order_items` table has the following attributes:

- Columns: `order_id` and `line_item_id` (a composite primary key), `product_id`, `unit_price`, `quantity`. The table also has a composite unique key on `order_id` and `product_id`.
- Relationships:
  - Column `product_id` relates each row of the table `order_items` to exactly one value of `product_id` in the `products` table.
  - Each `order_items` record is associated with a record in `orders` table through the `order_id.`

The `orders` table has the following attributes:

- Columns: `order_id` (primary key), `order_datetime`, `customer_id`, `order_status`, `store_id`.
- Relationships:
  - Column `order_id` relates each row of the table `orders` to none or more rows of `order_id` in the `order_items` table.
  - Column `customer_id` relates none or more rows of the table `orders` to the corresponding values in the `customer_id` column of the table `customers`.
  - Column `store_id` relates none or more rows of the table `orders` to the corresponding values in the `store_id` column of the table `stores`.

The `stores` table has the following attributes:

- Columns: `store_id` (primary key), `store_name`,`web_address`, `physical_address`, `latitude`,` longitude`, `logo`, `logo_mime_type`, `logo_charset`, `logo_filename`,` logo_last_updated`.
- Relationships:
  - Column `store_id` relates each row of the table `stores` to none or more rows of `store_id` in the `customers` table.
