# Description of the illustration alter_materialized_view.eps

    ALTER MATERIALIZED VIEW
      [ schema. ] materialized_view
      [ physical_attributes_clause
      | modify_mv_column_clause
      | table_compression
      | inmemory_table_clause
      | LOB_storage_clause [, LOB_storage_clause ]...
      | modify_LOB_storage_clause [, modify_LOB_storage_clause ]...
      | alter_table_partitioning
      | parallel_clause
      | logging_clause
      | allocate_extent_clause
      | deallocate_unused_clause
      | shrink_clause
      | { CACHE | NOCACHE }
      ]
      [ alter_iot_clauses ]
      [ USING INDEX physical_attributes_clause ]
      [ MODIFY scoped_table_ref_constraint
      | alter_mv_refresh
      ]
      [ evaluation_edition_clause ]
      [ { ENABLE | DISABLE } ON QUERY COMPUTATION ]
      [ alter_query_rewrite_clause
      | COMPILE
      | CONSIDER FRESH
      | annotations_clause
      ]
