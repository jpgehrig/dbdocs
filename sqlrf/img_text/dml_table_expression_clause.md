# Description of the illustration dml_table_expression_clause.eps

    { [ schema. ]
      { table
        [ partition_extension_clause
        | @ dblink
        ]
      | { view | materialized view } [ @ dblink ]
      }
    | ( subquery [ subquery_restriction_clause ] )
    | table_collection_expression
    }
