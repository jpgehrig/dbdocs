# Description of the illustration modify_list_partition.eps

    MODIFY partition_extended_name
      { partition_attributes
      | { ADD | DROP } VALUES ( list_values )
      | { add_range_subpartition
        | add_list_subpartition
        | add_hash_subpartition
        }
      | coalesce_table_subpartition
      | [ REBUILD ] UNUSABLE LOCAL INDEXES
      | read_only_clause
      | indexing_clause
      }
