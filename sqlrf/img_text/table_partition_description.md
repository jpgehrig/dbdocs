# Description of table_partition_description

     [ { INTERNAL | EXTERNAL } ]
    [ deferred_segment_creation ]
    [ read_only_clause ]
    [ indexing_clause ]
    [ segment_attributes_clause ]
    [ table_compression | prefix_compression ]
    [ inmemory_clause ]
    [ ilm_clause ]
    [ OVERFLOW [ segment_attributes_clause ] ]
    [ { LOB_storage_clause
      | varray_col_properties
      | nested_table_col_properties
      }...
    ]
