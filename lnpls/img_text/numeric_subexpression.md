# Description of the illustration numeric_subexpression.eps

     [ + | - ]
     { collection . { COUNT
                    | FIRST
                    | LAST
                    | LIMIT
                    | { NEXT | PRIOR } ( index )
                    }
     | named_cursor%ROWCOUNT
     | numeric_constant
     | numeric_function_call
     | numeric_literal
     | numeric_variable
     | placeholder
     | SQL%{ROWCOUNT | BULK_ROWCOUNT ( index )}
     }
     [ ** exponent ]
