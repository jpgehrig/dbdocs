# Description of the illustration list_partitions.eps

    PARTITION BY LIST ( column [, column]... )
    [ AUTOMATIC [ STORE IN ( tablespace [, tablespace ]... ) ] ]
    (PARTITION [ partition ]
        list_values_clause table_partition_description
      [, PARTITION [ partition ]
            list_values_clause table_partition_description
            [ external_part_subpart_data_props ]
      ]...
    )
