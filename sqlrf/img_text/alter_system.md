# Description of alter_system

    ALTER SYSTEM
      { archive_log_clause
      | checkpoint_clause
      | check_datafiles_clause
      | distributed_recov_clauses
      | FLUSH { SHARED_POOL | GLOBAL CONTEXT | BUFFER_CACHE | FLASH_CACHE
                    | REDO TO target_db_name [ [ NO ] CONFIRM APPLY ] }
      | end_session_clauses
      | SWITCH LOGFILE
      | { SUSPEND | RESUME }
      | quiesce_clauses
      | rolling_migration_clauses
      | rolling_patch_clauses
      | security_clauses
      | affinity_clauses
      | shutdown_dispatcher_clause
      | REGISTER
      | SET alter_system_set_clause
            [ alter_system_set_clause ]...
      | RESET alter_system_reset_clause
              [ alter_system_reset_clause ]...
      | RELOCATE CLIENT client_id
      | cancel_sql_clause
      | FLUSH PASSWORDFILE_METADATA_CACHE
      } ;
