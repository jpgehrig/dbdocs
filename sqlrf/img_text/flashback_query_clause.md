# Description of the illustration flashback_query_clause.eps

    { VERSIONS BETWEEN { SCN | TIMESTAMP }
        { expr | MINVALUE } AND { expr | MAXVALUE }
    | VERSIONS PERIOD FOR valid_time_column BETWEEN
        { expr | MINVALUE } AND { expr | MAXVALUE }
    | AS OF { SCN | TIMESTAMP } expr
    | AS OF PERIOD FOR valid_time_column expr
    }
