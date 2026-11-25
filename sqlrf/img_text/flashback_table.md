# Description of the illustration flashback_table.eps

    FLASHBACK TABLE
       [ schema. ] table
         [, [ schema. ] table ]...
       TO { { { SCN | TIMESTAMP } expr
            | RESTORE POINT restore_point
            } [ { ENABLE | DISABLE } TRIGGERS ]
          | BEFORE DROP [ RENAME TO table ]
          } ;
