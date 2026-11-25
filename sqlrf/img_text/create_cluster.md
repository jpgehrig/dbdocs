# Description of the illustration create_cluster.eps

    CREATE CLUSTER [ IF NOT EXISTS ] [ schema. ] cluster
      (column datatype [ COLLATE column_collation_name ] [ SORT ]
        [, column datatype [ COLLATE column_collation_name ] [ SORT ] ]...
      )
      [ SHARING "=" ( METADATA | NONE ) ]
      [ { physical_attributes_clause
        | SIZE size_clause
        | TABLESPACE tablespace
        | { INDEX
          | [ SINGLE TABLE ]
            HASHKEYS integer [ HASH IS expr ]
          }
        }...
      ]
      [ parallel_clause ]
      [ NOROWDEPENDENCIES | ROWDEPENDENCIES ]
      [ CACHE | NOCACHE ] [ cluster_range_partitions ]
