# Description of the illustration drop_constraint_clause.eps

    (
      DROP ( ( PRIMARY KEY
             | UNIQUE "(" (column)... ")"
             | CONSTRAINT constraint_name )
             [ CASCADE ] [( KEEP | DROP ) INDEX ]
           )
           [ ONLINE ]
    )
