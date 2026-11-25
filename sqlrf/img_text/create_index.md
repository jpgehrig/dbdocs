# Description of the illustration create_index.eps

    CREATE [ UNIQUE | BITMAP ] INDEX [ IF NOT EXISTS ] [ schema. ] index
      ON { cluster_index_clause
         | table_index_clause
         | bitmap_join_index_clause
         }
    [ USABLE | UNUSABLE ]
    [ { DEFERRED | IMMEDIATE } INVALIDATION ] ;
