# Description of alter_audit_policy

    ALTER AUDIT POLICY policy
      [ ADD [ privilege_audit_clause ] [ action_audit_clause ] [ role_audit_clause ]
       [ ONLY TOPLEVEL ] ]
      [ DROP [ privilege_audit_clause ] [ action_audit_clause ] [ role_audit_clause ]
       [ ONLY TOPLEVEL ] ]
      [ CONDITION { DROP | 'audit_condition'
        EVALUATE PER { STATEMENT  | SESSION | INSTANCE } } ];
