# Description of the illustration conditional_insert_clause.eps

    [ ALL | FIRST ]
    WHEN condition
    THEN insert_into_clause
      [ values_clause ]
      [ error_logging_clause ]
      [ insert_into_clause [ values_clause ] [ error_logging_clause ] ]...
    [ WHEN condition
      THEN insert_into_clause
        [ values_clause ]
        [ error_logging_clause ]
        [ insert_into_clause [ values_clause ] [ error_logging_clause ] ]...
    ]...
    [ ELSE insert_into_clause
      [ values_clause ]
      [ error_logging_clause ]
       [ insert_into_clause [ values_clause ] [ error_logging_clause ] ]...
    ]
