# Remove this title, leave empty.

The image shows a flow from a source table on the source database, through a series of steps, to duplicated tables on three database shards. The first step shows the source table pointing to the Data Pump. Then the Data Pump points to shard catalog (coordinator) where the table, now called duplicated table, has been loaded. From the shard catalog there are three arrows pointing from the duplicated table loaded there to the same duplicated table on the three database shards.
