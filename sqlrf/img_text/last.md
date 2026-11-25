# Description of the illustration last.eps

    aggregate_function KEEP
      (DENSE_RANK LAST ORDER BY
        expr [ DESC | ASC ]
             [ NULLS { FIRST | LAST } ]
        [, expr [ DESC | ASC ]
                [ NULLS { FIRST | LAST } ]
        ]...
      )
      [ OVER ( [query_partition_clause] ) ]
