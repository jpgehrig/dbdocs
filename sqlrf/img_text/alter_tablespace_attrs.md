# Description of the illustration alter_tablespace_attrs.eps

    { default_tablespace_params
    | MINIMUM EXTENT size_clause
    | RESIZE size_clause
    | COALESCE
    | SHRINK SPACE [ KEEP size_clause ]
    | RENAME TO new_tablespace_name
    | { BEGIN | END } BACKUP
    | datafile_tempfile_clauses
    | tablespace_logging_clauses
    | tablespace_group_clause
    | tablespace_state_clauses
    | autoextend_clause
    | flashback_mode_clause
    | tablespace_retention_clause
    | alter_tablespace_encryption
    }
