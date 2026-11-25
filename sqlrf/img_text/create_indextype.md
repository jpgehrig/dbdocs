# Description of the illustration create_indextype.eps

    CREATE [ OR REPLACE ] INDEXTYPE [ IF NOT EXISTS ] [ schema. ] indextype
      [ SHARING "=" ( METADATA | NONE ) ]
      FOR [ schema. ] operator (parameter_type [, parameter_type ]...)
            [, [ schema. ] operator (parameter_type [, parameter_type ]...)
            ]...
      using_type_clause
      [WITH LOCAL [RANGE] PARTITION ]
      [ storage_table_clause ]
