# Description of the illustration controlfile_clauses.eps

    CREATE { [ LOGICAL | PHYSICAL ] STANDBY | FAR SYNC INSTANCE }
      CONTROLFILE AS
      'filename' [ REUSE ]
    | BACKUP CONTROLFILE TO
      { 'filename' [ REUSE ]
      | trace_file_clause
      }
