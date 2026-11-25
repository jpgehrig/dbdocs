# Description of the illustration merge_table_subpartitions.eps

    MERGE SUBPARTITIONS subpartition_or_key_value
       { , subpartition_or_key_value [, subpartition_or_key_value ]...
       | TO subpartition_or_key_value }
       [ INTO { range_subpartition_desc
              | list_subpartition_desc
              }
       ]
       [ filter_condition ]
       [ dependent_tables_clause ]
       [ update_index_clauses ]
       [ parallel_clause ]
       [ allow_disallow_clustering ]
