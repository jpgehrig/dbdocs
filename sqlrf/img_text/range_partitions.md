# Description of the illustration range_partitions.eps

    PARTITION BY RANGE (column[, column ]...)
      [ INTERVAL ( expr ) [ STORE IN ( tablespace [, tablespace]...) ]]
    ( PARTITION [ partition ]
        range_values_clause table_partition_description
          [, PARTITION [ partition ]
            range_values_clause table_partition_description
            [ external_part_subpart_data_props ]
          ]...
    )
