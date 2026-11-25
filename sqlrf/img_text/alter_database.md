# Description of alter_database

    ALTER DATABASE [ database ]
      { startup_clauses
      | recovery_clauses
      | database_file_clauses
      | logfile_clauses
      | controlfile_clauses
      | standby_database_clauses
      | default_settings_clauses
      | instance_clauses
      | security_clause
      | prepare_clause
      | drop_mirror_copy
      | lost_write_protection
      | cdb_fleet_clauses
      | property_clause
      } ;
