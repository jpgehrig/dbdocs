# Description of the illustration on_list_partitioned_table.eps

    ( PARTITION
        [ partition ]
        [ { segment_attributes_clause
          | index_compression
          }...
        ] [ USABLE | UNUSABLE ]
          [, PARTITION
               [ partition ]
               [ { segment_attributes_clause
                 | index_compression
                 }...
               ] [ USABLE | UNUSABLE ]
          ]...
    )
