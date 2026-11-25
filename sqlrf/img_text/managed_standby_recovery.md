# Description of the illustration managed_standby_recovery.eps

    RECOVER
    { MANAGED STANDBY DATABASE
        [ { USING ARCHIVED LOGFILE
          | DISCONNECT [FROM SESSION]
          | NODELAY
          | UNTIL CHANGE integer
          | UNTIL CONSISTENT
          | USING INSTANCES { ALL | integer }
          | parallel_clause
          }...
        | FINISH
        | CANCEL
        ]
    | TO LOGICAL STANDBY { db_name | KEEP IDENTITY }
    }
