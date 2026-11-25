# Description of the illustration commit_switchover_clause.eps

    { PREPARE | COMMIT } TO SWITCHOVER
    [ TO { { [ PHYSICAL | LOGICAL ] PRIMARY
         | [ PHYSICAL ] STANDBY
         } [ { WITH | WITHOUT } SESSION SHUTDOWN
             { WAIT | NOWAIT }
           ]
         | LOGICAL STANDBY
         }
    | CANCEL
    ]
