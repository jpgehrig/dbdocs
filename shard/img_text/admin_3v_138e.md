# Description for illustration admin_3v_138d

The image admin_3v_138d shows how the Customers, Orders and Line Items tables are sharded by the Customer key into shards, each containing the rows from those tables pertaining to a single customer. The image also shows a Products table which is duplicated on all of the shards, so all of the rows from that table appear in each shard.
