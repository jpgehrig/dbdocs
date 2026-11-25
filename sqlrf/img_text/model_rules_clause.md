# Description of the illustration model_rules_clause.eps

    [ RULES
      [ { UPDATE | UPSERT [ ALL ] } ]
      [ { AUTOMATIC | SEQUENTIAL } ORDER ]
      [ model_iterate_clause ]
    ]
    ( [ { UPDATE | UPSERT [ ALL ] } ]
    cell_assignment [ order_by_clause ] = expr
      [,  [ { UPDATE | UPSERT [ ALL ] } ]
        cell_assignment [ order_by_clause ] = expr
      ]...
    )
