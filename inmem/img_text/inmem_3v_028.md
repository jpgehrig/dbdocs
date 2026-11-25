#

This example shows an order table in the center, and four IM column stores arranged around it. The orders table is partitioned by hash on the order_id column. The column has hashes 0, 1, 2, 3, 4. Each hash value points to a different IM column store.
