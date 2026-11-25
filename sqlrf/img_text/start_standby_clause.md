# Description of the illustration start_standby_clause.eps

    START LOGICAL STANDBY APPLY
    [ IMMEDIATE ]
    [ NODELAY ]
    [ NEW PRIMARY dblink
    | INITIAL [ scn_value ]
    | { SKIP FAILED TRANSACTION | FINISH }
    ]
