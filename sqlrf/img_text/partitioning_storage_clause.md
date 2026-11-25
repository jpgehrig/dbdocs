# Description of the illustration partitioning_storage_clause.eps

    [ { { TABLESPACE tablespace | TABLESPACE SET tablespace_set }
      | OVERFLOW [ TABLESPACE tablespace] | TABLESPACE SET tablespace_set ]
      | table_compression
      | index_compression
      | inmemory_clause
      | ilm_clause
      | LOB_partitioning_storage
      | VARRAY varray_item STORE AS [SECUREFILE | BASICFILE] LOB LOB_segname
      }...
    ]
