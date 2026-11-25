# Description of the illustration modify_table_subpartition.eps

    MODIFY subpartition_extended_name
    { allocate_extent_clause
    | deallocate_unused_cluse
    | shrink_clause
    | { { LOB LOB_item | VARRAY varray } (modify_LOB_parameters) }...
    | [ REBUILD ] UNUSABLE LOCAL INDEXES
    | { ADD | DROP } VALUES ( list_values )
    | read_only_clause
    | indexing_clause
    }
