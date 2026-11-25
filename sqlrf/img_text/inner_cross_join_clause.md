# Description of the illustration inner_cross_join_clause.eps

    { [ INNER ] JOIN table_reference
        { ON condition
        | USING (column [, column ]...)
        }
    | { CROSS
      | NATURAL [ INNER ]
      }
      JOIN table_reference
    }
