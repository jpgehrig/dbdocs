# Description of the illustration alter_indextype.eps

    ALTER INDEXTYPE [ IF EXISTS ] [ schema. ] indextype
      { { ADD | DROP } [ schema. ] operator ( parameter_types )
          [ , { ADD | DROP } [schema. ] operator ( parameter_types ) ]... [ using_type_clause ]
      | COMPILE
      }
      [ WITH LOCAL [ RANGE ] PARTITION ] [ storage_table_clause ]
