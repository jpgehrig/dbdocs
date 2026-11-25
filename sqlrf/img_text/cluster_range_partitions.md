# Description of the illustration cluster_range_partitions.eps

    PARTITION BY RANGE (column[, column ]...)
    ( PARTITION [ partition ]
        range_values_clause table_partition_description
          [, PARTITION [ partition ]
            range_values_clause table_partition_description
          ]...
    )
