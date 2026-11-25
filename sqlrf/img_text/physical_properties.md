# Description of physical_properties

    { [ deferred_segment_creation ] segment_attributes_clause [ table_compression ]
        [ inmemory_table_clause ] [ ilm_clause ]
    | [ deferred_segment_creation ] ORGANIZATION
      { HEAP [ segment_attributes_clause ] heap_org_table_clause
      | INDEX [ segment_attributes_clause ] index_org_table_clause
      | EXTERNAL PARTITION ATTRIBUTES external_table_clause
        [ REJECT LIMIT ]
      }
    | CLUSTER cluster (column [, column ]...)
    }
