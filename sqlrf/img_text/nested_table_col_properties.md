# Description of the illustration nested_table_col_properties.eps

    NESTED TABLE
    { nested_item | COLUMN_VALUE }
    [ substitutable_column_clause ]
    [ LOCAL | GLOBAL ]
    STORE AS storage_table
    [ ( { (object_properties)
        | [ physical_properties ]
        | [ column_properties ]
        }...
      )
    ]
    [ RETURN [ AS ]  { LOCATOR | VALUE } ]
