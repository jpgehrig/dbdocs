# Description of the illustration pdb_settings_clauses.eps

    { [ pdb_name ]
      { DEFAULT EDITION = edition_name
      | SET DEFAULT ( BIGFILE | SMALLFILE ) TABLESPACE
      | DEFAULT TABLESPACE tablespace_name
      | DEFAULT TEMPORARY TABLESPACE { tablespace | tablespace_group_name }
      | RENAME GLOBAL_NAME TO database.domain [. domain ]...
      | set_time_zone_clause
      | database_file_clauses
      | supplemental_db_logging
      | pdb_storage_clause
      | pdb_logging_clauses
      | pdb_refresh_mode_clause
      | pdb_refresh_switchover_clause
      | REFRESH [ pdb_refresh_switchover_clause ]
        | SET CONTAINER_MAP = 'map_object'
      }
    }
    | CONTAINERS { DEFAULT TARGET = { (container_name) | NONE }
                 | HOST "=" "'" hostname "'"
                 | PORT "=" number
                 }
