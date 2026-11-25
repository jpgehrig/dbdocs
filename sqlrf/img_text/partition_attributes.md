# Description of the illustration partition_attributes.eps

    [ { physical_attributes_clause
      | logging_clause
      | allocate_extent_clause
      | deallocate_unused_clause
      | shrink_clause
      }...
    ]
    [ OVERFLOW
      { physical_attributes_clause
      | logging_clause
      | allocate_extent_clause
      | deallocate_unused_clause
      }...
    ]
    [ table_compression ]
    [ inmemory_clause ]
    [ { { LOB LOB_item | VARRAY varray } (modify_LOB_parameters) }...]
