# Description of the illustration alter_view.eps

    ALTER VIEW [ schema. ] view
      { ADD out_of_line_constraint
      | MODIFY CONSTRAINT constraint
          { RELY | NORELY }
      | DROP { CONSTRAINT constraint
             | PRIMARY KEY
             | UNIQUE (column [, column ]...)
             }
      | COMPILE
      | { READ ONLY | READ WRITE }
      | { EDITIONABLE | NONEDITIONABLE }
      | annotations_clause
      }
