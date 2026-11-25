# Description of the illustration admin590.eps

This illustration shows that the `product_information` table and the `product_descriptions` table have a one to many relationship through the `product_id` column.

The `product_information` table and the `inventories` table have a one to many relationship through the `product_id` column.

The `inventories` table and the `warehouses` table have a many to one relationship through the `warehouse_id` column.

The `locations` table and the `warehouses` table have a one to many relationship through the `location_id` column.

The primary key of the `product_information` table is the `product_id` column.

The primary key of the `product_descriptions` table includes the `product_id` and `language_id` columns.

The primary key of the `inventories` table includes the `product_id` and `warehouse_id` columns.

The primary key of the `warehouses` table is the `warehouse_id` column.

The primary key of the `locations` table is the `location_id` column.
