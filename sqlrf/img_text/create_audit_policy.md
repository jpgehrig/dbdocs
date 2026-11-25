# Description of create_audit_policy

    CREATE AUDIT POLICY policy
      [ privilege_audit_clause ] [ action_audit_clause ] [ role_audit_clause ]
      [ WHEN 'audit_condition' EVALUATE PER
        { STATEMENT | SESSION | INSTANCE } ]
      [ ONLY TOPLEVEL ]
      [ CONTAINER = { ALL | CURRENT } ] ;
