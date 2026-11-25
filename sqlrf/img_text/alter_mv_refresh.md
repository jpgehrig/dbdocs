# Description of the illustration alter_mv_refresh.eps

    REFRESH
       { { FAST | COMPLETE | FORCE }
       | ON { DEMAND | COMMIT }
       | { START WITH | NEXT } date
       | WITH PRIMARY KEY
       | USING
            { DEFAULT MASTER ROLLBACK SEGMENT
            | MASTER ROLLBACK SEGMENT rollback_segment
            }
       | USING { ENFORCED | TRUSTED } CONSTRAINTS
       }
