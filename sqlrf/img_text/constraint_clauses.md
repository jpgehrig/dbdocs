# Description of the illustration constraint_clauses.eps

    { ADD { { out_of_line_constraint }...
          | out_of_line_REF_constraint
          }
    | MODIFY { CONSTRAINT constraint_name
             | PRIMARY KEY
             | UNIQUE (column [, column ]...)
             } constraint_state [ CASCADE ]
    | RENAME CONSTRAINT old_name TO new_name
    | { drop_constraint_clause }...
    }
