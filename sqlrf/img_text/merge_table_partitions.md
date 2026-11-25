# Description of the illustration merge_table_partitions.eps

    MERGE PARTITIONS partition_or_key_value
       { , partition_or_key_value [, partition_or_key_value ]...
       | TO partition_or_key_value }
       [ INTO partition_spec ]
       [ filter_condition ]
       [ dependent_tables_clause ]
       [ update_index_clauses ]
       [ parallel_clause ]
       [ allow_disallow_clustering ]
