# Description of the illustration query_block.eps

      [ with_clause ]
    SELECT [ hint ] [ { { DISTINCT | UNIQUE } | ALL } ] select_list
      FROM { table_reference | join_clause | ( join_clause ) | inline_analytic_view }
             [ , { table_reference | join_clause | (join_clause) | inline_analytic_view} ] ...
      [ where_clause ]
      [ hierarchical_query_clause ]
      [ group_by_clause ]
      [ model_clause ]
