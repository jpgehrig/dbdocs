# Description of the illustration global_partitioned_index.eps

    GLOBAL PARTITION BY
       { RANGE (column_list)
            (index_partitioning_clause)
       | HASH (column_list)
            { individual_hash_partitions
            | hash_partitions_by_quantity
            }
       }
