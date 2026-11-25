# Description of the illustration unified_audit.eps

    AUDIT
      { POLICY policy
        [ { BY user [, user]... }
        | { EXCEPT user [, user]... }
        | by_users_with_roles ]
        [ WHENEVER [ NOT ] SUCCESSFUL ]
      }
      |
      { CONTEXT NAMESPACE namespace ATTRIBUTES attribute [, attribute ]...
          [, CONTEXT NAMESPACE namespace ATTRIBUTES attribute [, attribute ]... ]...
        [ BY user [, user]... ]
      } ;
