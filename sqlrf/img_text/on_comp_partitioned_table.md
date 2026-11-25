# Description of the illustration on_comp_partitioned_table.eps

    [ STORE IN ( tablespace [, tablespace ]... ) ]
    ( PARTITION
        [ partition ]
        [ { segment_attributes_clause
          | index_compression
          }...
        ] [ USABLE | UNUSABLE ] [ index_subpartition_clause ]
          [, PARTITION
               [ partition ]
               [ { segment_attributes_clause
                 | index_compression
                 }...
               ] [ USABLE | UNUSABLE ] [ index_subpartition_clause ]
           ]...
    )
