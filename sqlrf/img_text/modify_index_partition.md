# Description of the illustration modify_index_partition

    MODIFY PARTITION partition
    { { deallocate_unused_clause
      | allocate_extent_clause
      | physical_attributes_clause
      | logging_clause
      | index_compression
      }...
    | PARAMETERS ('ODCI_parameters')
    | COALESCE [ CLEANUP ] [  parallel_clause ]
    | UPDATE BLOCK REFERENCES
    | UNUSABLE
    }
