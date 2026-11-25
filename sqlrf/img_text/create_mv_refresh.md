# Description of the illustration create_mv_refresh.eps

    { REFRESH
      { { FAST | COMPLETE | FORCE }
      | { ON DEMAND
        | ON COMMIT
        | ON STATEMENT
        }
      | { START WITH date |
          NEXT date
        }...
      | WITH { PRIMARY KEY | ROWID }
      | USING
         { DEFAULT [ MASTER | LOCAL ] ROLLBACK SEGMENT
         | [ MASTER | LOCAL ] ROLLBACK SEGMENT rollback_segment
         }...
      | USING
         { ENFORCED | TRUSTED } CONSTRAINTS
      }...
    | NEVER REFRESH
    }
