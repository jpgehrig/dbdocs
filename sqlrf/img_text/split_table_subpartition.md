# Description of the illustration split_table_subpartition.eps

    SPLIT subpartition_extended_name
      { AT ( literal [, literal]... )
        [ INTO ( range_subpartition_desc, range_subpartition_desc ) ]
      | VALUES ( list_values )
        [ INTO ( list_subpartition_desc, list_subpartition_desc ) ]
      | INTO ( { range_subpartition_desc [, range_subpartition_desc ]...
               | list_subpartition_desc [, list_subpartition_desc ]... }
             , subpartition_spec )
      } [ filter_condition ]
        [ dependent_tables_clause ]
        [ update_index_clauses ]
        [ parallel_clause ]
        [ allow_disallow_clustering ]
        [ ONLINE ]
