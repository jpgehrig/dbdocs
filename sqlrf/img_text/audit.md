# Description of the illustration audit.eps

    AUDIT
      { audit_operation_clause [ auditing_by_clause | IN SESSION CURRENT ]
      | audit_schema_object_clause
      | NETWORK
      | DIRECT_PATH LOAD [ auditing_by_clause ]
      } [ BY { SESSION | ACCESS } ]
        [ WHENEVER [ NOT ] SUCCESSFUL ]
        [ CONTAINER = { CURRENT | ALL } ]
    ;
