# Description of the illustration alter_table_properties.eps

    { { { physical_attributes_clause
        | logging_clause
        | table_compression
        | inmemory_table_clause
        | ilm_clause
        | supplemental_table_logging
        | allocate_extent_clause
        | deallocate_unused_clause
        | { CACHE | NOCACHE }
        | RESULT_CACHE ( MODE {DEFAULT | FORCE} )
        | upgrade_table_clause
        | records_per_block_clause
        | parallel_clause
        | row_movement_clause
        | flashback_archive_clause
        }...
      | RENAME TO new_table_name
      } [ alter_iot_clauses ] [ alter_XMLSchema_clause ]
    | { shrink_clause
      | READ ONLY
      | READ WRITE
      | REKEY encryption_spec
      | DEFAULT COLLATION collation_name
      | [NO] ROW ARCHIVAL
      | ADD attribute_clustering_clause
      | MODIFY CLUSTERING [ clustering_when ] [ zonemap_clause ]
      | DROP CLUSTERING
      | annotations_clause
      }
    }
