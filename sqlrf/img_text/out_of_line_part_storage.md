# Description of the illustration out_of_line_part_storage.eps

    PARTITION partition
      { nested_table_col_properties | LOB_storage_clause | varray_col_properties }
        [ nested_table_col_properties | LOB_storage_clause | varray_col_properties ]...
    [ ( SUBPARTITION subpartition
       { nested_table_col_properties | LOB_storage_clause | varray_col_properties }
         [ nested_table_col_properties | LOB_storage_clause | varray_col_properties
         ]...
        [, SUBPARTITION subpartition
         { nested_table_col_properties | LOB_storage_clause | varray_col_properties }
           [ nested_table_col_properties | LOB_storage_clause | varray_col_properties
           ]...
        ]...
      )
    ]
