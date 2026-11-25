# Description of create_zonemap_as_subquery

    CREATE MATERIALIZED ZONEMAP [ IF NOT EXISTS ]
      [ schema. ] zonemap_name
      [ zonemap_attributes ]
      [ zonemap_refresh_clause ]
      [ { ENABLE | DISABLE } PRUNING ]
      AS query_block
