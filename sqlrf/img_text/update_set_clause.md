# Description of the illustration update_set_clause.eps

    SET
    { { (column [, column ]...) = (subquery)
      | column = { expr | (subquery) | DEFAULT }
      }
         [, { (column [, column]...) = (subquery)
            | column = { expr | (subquery) | DEFAULT }
            }
         ]...
    | VALUE (t_alias) = { expr | (subquery) }
    }
