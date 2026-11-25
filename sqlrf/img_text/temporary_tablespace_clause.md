# Description of the illustration temporary_tablespace_clause.eps

    { { TEMPORARY TABLESPACE }
    | { LOCAL TEMPORARY TABLESPACE FOR { ALL | LEAF } }
    } tablespace
    [ TEMPFILE file_specification [, file_specification ]... ]
    [ tablespace_group_clause ]
    [ extent_management_clause ]
