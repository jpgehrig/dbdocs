# Description of the illustration move_table_clause.eps

    MOVE
       [ filter_condition ]
       [ ONLINE ]
       [ segment_attributes_clause ]
       [ table_compression ]
       [ index_org_table_clause ]
       [ { lob_storage_clause | json_storage_clause | varray_col_properties }... ]
       [ parallel_clause ]
       [ allow_disallow_clustering ]
       [ UPDATE INDEXES
         [ ( index { segment_attributes_clause
                   | update_index_partition }
             [, index { segment_attributes_clause
                      | update_index_partition } ]...
           )
         ]
       ]
