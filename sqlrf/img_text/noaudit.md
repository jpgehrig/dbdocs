# Description of the illustration noaudit.eps

    NOAUDIT
       { audit_operation_clause [ auditing_by_clause ]
       | audit_schema_object_clause
       | NETWORK
       | DIRECT_PATH LOAD [ auditing_by_clause ]
       }
       [ WHENEVER [ NOT ] SUCCESSFUL ]
       [ CONTAINER = { CURRENT | ALL } ] ;
