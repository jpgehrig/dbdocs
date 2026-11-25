# Description of the illustration admin589.eps

This illustration shows the `order_items` master table and the `inventories` master table. The `order_items` table has a primary key that includes both the `order_id` column and the `line_item_id` column. The `inventories` table has a primary key that includes both the `product_id` column and the `warehouse_id` column. The `product_id` column exists in both tables. There is a many to many relationship between the `order_items` and `inventories` tables because many order items can be available in many inventories.
