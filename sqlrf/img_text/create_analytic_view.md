# Description of the illustration create_analytic_view.eps

    CREATE [ OR REPLACE ] [ { FORCE | NOFORCE } ] ANALYTIC VIEW
        [ IF NOT EXISTS ] [ schema. ] analytic_view
        [ SHARING "=" ( METADATA | NONE ) ]
        [ classification_clause ]...
        using_clause
        dim_by_clause
        measures_clause
        [ default_measure_clause ]
        [ default_aggregate_clause ]
        [ cache_clause ]
    ;
