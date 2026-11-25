# Description of the illustration default_settings_clauses.eps

    { DEFAULT EDITION = edition_name
    | SET DEFAULT { BIGFILE | SMALLFILE } TABLESPACE
    | DEFAULT TABLESPACE tablespace
    | DEFAULT [ LOCAL ] TEMPORARY TABLESPACE { tablespace | tablespace_group_name }
    | RENAME GLOBAL_NAME TO database.domain [.domain ]...
    | ENABLE BLOCK CHANGE TRACKING [ USING FILE 'filename' [ REUSE ] ]
    | DISABLE BLOCK CHANGE TRACKING
    | [NO] FORCE FULL DATABASE CACHING
    | CONTAINERS DEFAULT TARGET = { (container_name) | NONE }
    | flashback_mode_clause
    | undo_mode_clause
    | set_time_zone_clause
    }
