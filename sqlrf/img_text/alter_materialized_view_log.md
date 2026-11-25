# Description of the illustration alter_materialized_view_log.eps

    ALTER MATERIALIZED VIEW LOG [ IF EXISTS ] [ FORCE ]
      ON [ schema. ]table
      [ physical_attributes_clause
      | add_mv_log_column_clause
      | alter_table_partitioning
      | parallel_clause
      | logging_clause
      | allocate_extent_clause
      | shrink_clause
      | move_mv_log_clause
      | { CACHE | NOCACHE }
      ] [ mv_log_augmentation ] [  mv_log_purge_clause ] [ for_refresh_clause ]
