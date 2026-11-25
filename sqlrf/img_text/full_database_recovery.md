# Description of the illustration full_database_recovery.eps

    [ STANDBY ] DATABASE
    [ { UNTIL { CANCEL
              | TIME date
              | CHANGE integer
              | CONSISTENT
              }
      | USING BACKUP CONTROLFILE
      }...
    ]
