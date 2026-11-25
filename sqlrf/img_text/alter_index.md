# Description of the illustration alter_index

    ALTER INDEX [ IF EXISTS ][ schema. ]index
      { { deallocate_unused_clause
        | allocate_extent_clause
        | shrink_clause
        | parallel_clause
        | physical_attributes_clause
        | logging_clause
        | partial_index_clause
        } ...
      | rebuild_clause
      | PARAMETERS ( 'ODCI_parameters' )
                   )
      | COMPILE
      | { ENABLE | DISABLE }
      | UNUSABLE [ ONLINE ] [ { DEFERRED | IMMEDIATE } INVALIDATION ]
      | VISIBLE | INVISIBLE
      | RENAME TO new_name
      | COALESCE [ CLEANUP ] [ ONLY ] [ parallel_clause ]
      | { MONITORING | NOMONITORING } USAGE
      | UPDATE BLOCK REFERENCES
      | alter_index_partitioning
      | annotations_clause
      }
