# Description of the illustration create_materialized_vw_log.eps

    CREATE MATERIALIZED VIEW LOG ON [ IF NOT EXISTS ] [ schema. ] table
      [ SHARING "=" ( METADATA | NONE ) ]
      [ physical_attributes_clause
      | TABLESPACE tablespace
      | logging_clause
      | { CACHE | NOCACHE }
      ]...
      [ parallel_clause ]
      [ table_partitioning_clauses ]
      [ WITH [ { OBJECT ID
             | PRIMARY KEY
             | ROWID
             | SEQUENCE
             | COMMIT SCN
             }
               [ { , OBJECT ID
                 | , PRIMARY KEY
                 | , ROWID
                 | , SEQUENCE
                 | , COMMIT SCN
                 }
               ]... ]
        (column [, column ]...)
        [ new_values_clause ]
      ] [ mv_log_purge_clause ] [ for_refresh_clause ]
