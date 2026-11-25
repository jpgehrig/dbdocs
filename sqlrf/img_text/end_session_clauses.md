# Description of the illustration end_session_clauses.eps

    { DISCONNECT SESSION 'session_id, serial_number'
         [ POST_TRANSACTION ]
    | KILL SESSION 'session_id, serial_number [, @ instance_id]'
    }
    [ IMMEDIATE | NOREPLAY ]
