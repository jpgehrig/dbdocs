# Description of the illustration admin_3v_130a.png

This illustration shows a graphical view of the table created by the statement in the preceding code example. This is an example of system-managed sharding by consistent hash with subpartitioning by range.

The illustration consists of three shards contained in a tablespace set tbs1.

Shard 1 contains tablespaces tbs1–1 and tbs1–2, each of which contain a partition, Partition 1 and Partition 2, respectively. Subpartitions of Partition 1 are shown in boxes 1, 2, 3, and 4 inside of the Partition 1 space, and subpartitions of Partitions 2 are shown in boxes 1, 2, 3, and 4 inside of the Partition 2 space.

Shards 2 and 3 follow a similar layout with four subpartitions shown contained within the parent partition in each tablespace.
