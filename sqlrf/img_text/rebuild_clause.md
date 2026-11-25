# Description of the illustration rebuild_clause.eps

    REBUILD
      [ { PARTITION partition
        | SUBPARTITION subpartition
        }
      | { REVERSE | NOREVERSE }
      ]
      [ parallel_clause
      | TABLESPACE tablespace
      | PARAMETERS ( 'ODCI_parameters' )
      | XMLIndex_parameters_clause
      | ONLINE
      | physical_attributes_clause
      | index_compression
      | logging_clause
      | partial_index_clause
      ]...
