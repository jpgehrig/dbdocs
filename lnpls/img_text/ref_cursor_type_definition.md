# Description of the illustration ref_cursor_type_definition.eps

    TYPE type IS REF CURSOR
      [ RETURN
        { {db_table_or_view | cursor | cursor_variable}%ROWTYPE
        | record%TYPE
        | record_type
        | ref_cursor_type
        }
      ] ;
