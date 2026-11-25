# Description of the illustration default_temp_tablespace.eps

    [ BIGFILE | SMALLFILE ] DEFAULT
    { { TEMPORARY TABLESPACE }
    | { LOCAL TEMPORARY TABLESPACE FOR { ALL | LEAF } }
    } tablespace
    [ TEMPFILE file_specification [, file_specification ]...]
    [ extent_management_clause ]
