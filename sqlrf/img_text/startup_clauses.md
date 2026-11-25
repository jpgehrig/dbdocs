# Description of the illustration startup_clauses.eps

    { MOUNT [ { STANDBY | CLONE } DATABASE ]
    | OPEN
      { [ READ WRITE ]
          [ RESETLOGS | NORESETLOGS ]
            [ UPGRADE | DOWNGRADE ]
      | READ ONLY
      }
    }
