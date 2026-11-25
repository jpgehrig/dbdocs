# Description of the illustration alter_materialized_zonemap.eps

    ALTER MATERIALIZED ZONEMAP [ IF EXISTS ] [ schema. ] zonemap_name
      { alter_zonemap_attributes
      | zonemap_refresh_clause
      | { ENABLE | DISABLE } PRUNING
      | COMPILE
      | REBUILD
      | UNUSABLE
      }
