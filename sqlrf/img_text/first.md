# Description of the illustration first.eps

    aggregate_function KEEP
       ( DENSE_RANK FIRST ORDER BY
        expr [ DESC | ASC ]
             [ NULLS { FIRST | LAST } ]
        [, expr [ DESC | ASC ]
                [ NULLS { FIRST | LAST } ]
        ]...
       )
       [ OVER ( [query_partition_clause] ) ]
