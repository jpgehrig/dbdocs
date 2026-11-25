# Description of the illustration merge_update_clause.eps

    WHEN MATCHED THEN
    UPDATE SET column = { expr | DEFAULT }
               [, column = { expr | DEFAULT } ]...
    [ where_clause ]
    [ DELETE where_clause ]
