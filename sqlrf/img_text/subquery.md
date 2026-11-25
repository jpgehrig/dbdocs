# Description of the illustration subquery.eps

    { query_block
    | subquery { UNION [ALL] | INTERSECT | MINUS } subquery
        [ { UNION [ALL] | INTERSECT | MINUS } subquery ]...
    | ( subquery )
    } [ order_by_clause ] [ row_limiting_clause ]
