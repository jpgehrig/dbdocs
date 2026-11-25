# Description of the illustration modify_lob_parameters.eps

    { storage_clause
    | PCTVERSION integer
    | FREEPOOLS integer
    | REBUILD FREEPOOLS
    | LOB_retention_clause
    | LOB_deduplicate_clause
    | LOB_compression_clause
    | { ENCRYPT encryption_spec | DECRYPT }
    | { CACHE
      | { NOCACHE | CACHE READS } [ logging_clause ]
      }
    | allocate_extent_clause
    | shrink_clause
    | deallocate_unused_clause
    } ...
