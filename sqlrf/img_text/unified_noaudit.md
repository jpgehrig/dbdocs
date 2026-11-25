# Description of unified_noaudit

    NOAUDIT
      { POLICY policy [ { BY user [, user]... } | by_users_with_roles ] }
      |
      { CONTEXT NAMESPACE namespace ATTRIBUTES attribute [, attribute ]...
          [, CONTEXT NAMESPACE namespace ATTRIBUTES attribute [, attribute ]... ]...
        [ BY user [, user]... ] [ WHENEVER [ NOT ] SUCCESSFUL ]
      } ;
