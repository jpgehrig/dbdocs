# Description of the illustration alter_external_table.eps

    { add_column_clause
    | modify_column_clauses
    | drop_column_clause
    | parallel_clause
    | external_table_data_props
    | REJECT LIMIT { integer | UNLIMITED }
    | PROJECT COLUMN { ALL | REFERENCED }
    }
      [ add_column_clause
      | modify_column_clauses
      | drop_column_clause
      | parallel_clause
      | external_table_data_props
      | REJECT LIMIT { integer | UNLIMITED }
      | PROJECT COLUMN { ALL | REFERENCED }
      ]...
