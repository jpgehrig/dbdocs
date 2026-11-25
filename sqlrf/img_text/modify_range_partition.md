# Description of the illustration modify_range_partition.eps

    MODIFY partition_extended_name
       { partition_attributes
       | { add_range_subpartition
         | add_hash_subpartition
         | add_list_subpartition
         }
       | coalesce_table_subpartition
       | alter_mapping_table_clause
       | [ REBUILD ] UNUSABLE LOCAL INDEXES
       | read_only_clause
       | indexing_clause
       }
