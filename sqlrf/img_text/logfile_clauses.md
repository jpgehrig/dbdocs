# Description of the illustration logfile_clauses.eps

    { { ARCHIVELOG [ MANUAL ]
      | NOARCHIVELOG
      }
    | [ NO ] FORCE LOGGING
    | SET STANDBY NOLOGGING FOR {DATA AVAILABILITY | LOAD PERFORMANCE}
    | RENAME FILE 'filename' [, 'filename' ]...
        TO 'filename'
    | CLEAR [ UNARCHIVED ]
        LOGFILE logfile_descriptor [, logfile_descriptor ]...
        [ UNRECOVERABLE DATAFILE ]
    | add_logfile_clauses
    | drop_logfile_clauses
    | switch_logfile_clause
    | supplemental_db_logging
    }
