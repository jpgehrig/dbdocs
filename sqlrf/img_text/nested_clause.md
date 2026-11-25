# Description of nested_clause

    table_reference (NESTED [PATH]) identifier
    [
    ("." [ JSON_object_key array_step ] ) |
    ("," JSON_basic_path_expression )
    ]
    [ JSON_table_on_error_clause ]
    [ JSON_table_on_empty_clause ]
     JSON_columns_clause
