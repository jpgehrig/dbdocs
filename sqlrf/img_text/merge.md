# Description of the illustration merge.eps

    MERGE [ hint ]
       INTO [ schema. ] { table | view } [ t_alias ]
       USING { [ schema. ] { table | view }
             | ( subquery )
             } [ t_alias ]
       ON ( condition )
       [ merge_update_clause ]
       [ merge_insert_clause ]
       [ error_logging_clause ] ;
