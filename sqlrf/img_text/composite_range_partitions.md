# Description of the illustration composite_range_partitions.eps

    PARTITION BY RANGE ( column [, column]... )
      [ INTERVAL ( expr ) [ STORE IN ( tablespace [, tablespace]... ) ]]
      { subpartition_by_range
      | subpartition_by_list
      | subpartition_by_hash
      }
    ( range_partition_desc [, range_partition_desc ]... )
