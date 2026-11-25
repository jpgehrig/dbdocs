# Description of the illustration query_table_expression.eps

    { query_name
    | [ schema. ]
      { table [ partition_extension_clause
              | @ dblink
              ]
      | { view | materialized view } [ @ dblink ]
      | analytic_view [ hierarchies_clause ] ) ]
      | hierarchy
      } [sample_clause]
    | [ LATERAL ] (subquery [ subquery_restriction_clause ])
    | table_collection_expression
    }
