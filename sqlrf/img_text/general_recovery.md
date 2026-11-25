# Description of the illustration general_recovery.eps

    RECOVER
    [ AUTOMATIC ]
    [ FROM 'location' ]
    { { full_database_recovery
      | partial_database_recovery
      | LOGFILE 'filename'
      }
      [ { TEST
        | ALLOW integer CORRUPTION
        | parallel_clause
        }...
      ]
    | CONTINUE [ DEFAULT ]
    | CANCEL
    }
