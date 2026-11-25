# Description of the illustration analyze.eps

    ANALYZE
      { { TABLE [ schema. ] table
        | INDEX [ schema. ] index
        } [ partition_extension_clause ]
      | CLUSTER [ schema. ] cluster
      }
      { validation_clauses
      | LIST CHAINED ROWS [ into_clause ]
      | DELETE [ SYSTEM ] STATISTICS
      } ;
