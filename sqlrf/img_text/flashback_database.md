# Description of the illustration flashback_database.eps

    FLASHBACK [ STANDBY ] [ PLUGGABLE ] DATABASE [ database ]
       { TO { { SCN | TIMESTAMP } expr
            | RESTORE POINT restore_point
            }
       }
       | { TO BEFORE { { SCN | TIMESTAMP } expr
                     | RESETLOGS
                     }
       } ;
