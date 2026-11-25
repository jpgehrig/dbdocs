# Description of the illustration create_materialized_view.eps

    CREATE MATERIALIZED VIEW [ IF NOT EXISTS ] [ schema. ] materialized_view
      [ OF [ schema. ] object_type ]
      [ ( { scoped_table_ref_constraint
          | column_alias [ENCRYPT [encryption_spec]]
          }
          [, { scoped_table_ref_constraint
             | column_alias [ENCRYPT [encryption_spec]]
             }
          ]...
        )
      ]
      [ DEFAULT COLLATION collation_name ]
      { ON PREBUILT TABLE
        [ { WITH | WITHOUT } REDUCED PRECISION ]
      | physical_properties materialized_view_props
      }
      [ USING INDEX
        [ physical_attributes_clause
        | TABLESPACE tablespace
        ]...
      | USING NO INDEX
      ]
      [ create_mv_refresh ]
      [ evaluation_edition_clause ]
      [ { ENABLE | DISABLE } ON QUERY COMPUTATION ]
      [ query_rewrite_clause ]
      [ annotations_clause ]
    AS subquery
