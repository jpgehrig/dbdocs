# Description of the illustration composite_hash_partitions.eps

    PARTITION BY HASH (column [, column ] ...)
      { subpartition_by_range
      | subpartition_by_list
      | subpartition_by_hash
      }
      { individual_hash_partitions
      | hash_partitions_by_quantity
      }
