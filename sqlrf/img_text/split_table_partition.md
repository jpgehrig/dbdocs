# Description of the illustration split_table_partition.eps

    SPLIT partition_extended_name
      { AT (literal [, literal]... )
        [ INTO ( range_partition_desc, range_partition_desc ) ]
      | VALUES ( list_values )
        [ INTO ( list_partition_desc, list_partition_desc ) ]
      | INTO ( { range_partition_desc [, range_partition_desc ]...
               | list_partition_desc [, list_partition_desc ]... }
             , partition_spec )
      } [ split_nested_table_part ]
        [ filter_condition ]
        [ dependent_tables_clause ]
        [ update_index_clauses ]
        [ parallel_clause ]
        [ allow_disallow_clustering ]
        [ ONLINE ]
