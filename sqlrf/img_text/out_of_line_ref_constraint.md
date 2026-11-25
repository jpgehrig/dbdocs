# Description of the illustration out_of_line_ref_constraint.eps

    { SCOPE FOR ({ ref_col | ref_attr })
        IS [ schema. ] scope_table
    | REF ({ ref_col | ref_attr }) WITH ROWID
    | [ CONSTRAINT constraint_name ] FOREIGN KEY
        ( { ref_col [, ref_col ] | ref_attr [, ref_attr ] } ) references_clause
        [ constraint_state ]
    }
