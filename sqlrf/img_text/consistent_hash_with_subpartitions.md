# Description of the illustration consistent_hash_with_subpartitions.eps

    PARTITION BY CONSISTENT HASH (column [, column ]...)
      { subpartition_by_range
      | subpartition_by_list
      | subpartition_by_hash
      }
      [ PARTITIONS AUTO ]
