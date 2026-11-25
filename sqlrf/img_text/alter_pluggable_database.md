# Description of alter_pluggable_database

    ALTER PLUGGABLE DATABASE
      { pdb_unplug_clause
      | pdb_settings_clauses
      | pdb_datafile_clause
      | pdb_recovery_clauses
      | pdb_change_state
      | pdb_change_state_from_root
      | application_clauses
      | snapshot_clauses
      | prepare_clause
      | drop_mirror_copy
      | lost_write_protection
      } ;
