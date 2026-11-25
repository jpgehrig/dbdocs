# Description of the illustration create_zonemap_on_table.eps

    CREATE MATERIALIZED ZONEMAP [ IF NOT EXISTS ]
      [ schema. ] zonemap_name
      [ zonemap_attributes ]
      [ zonemap_refresh_clause ]
      [ { ENABLE | DISABLE } PRUNING ]
      ON [ schema. ] { table | materialized_view } ( column [, column]... )
