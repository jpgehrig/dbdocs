# Description of the illustration drop_column_clause.eps

    { SET UNUSED { COLUMN column
                 | (column [, column ]...)
                 }
      [ { CASCADE CONSTRAINTS | INVALIDATE }... ]
      [ ONLINE ]
    | DROP { COLUMN column
           | (column [, column ]...)
           }
      [ { CASCADE CONSTRAINTS | INVALIDATE }... ]
      [ CHECKPOINT [ integer ] ]
    | DROP { UNUSED COLUMNS
           | COLUMNS CONTINUE
           }
      [ CHECKPOINT [ integer ] ]
    }
