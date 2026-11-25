# Description of the illustration mv_log_purge_clause.eps

    PURGE { IMMEDIATE [ SYNCHRONOUS | ASYNCHRONOUS ]
          | START WITH datetime_expr [ NEXT datetime_expr
                                     | REPEAT INTERVAL interval_expr
                                     ]
          | [ START WITH datetime_expr ] { NEXT datetime_expr
                                         | REPEAT INTERVAL interval_expr
                                         }
          }
