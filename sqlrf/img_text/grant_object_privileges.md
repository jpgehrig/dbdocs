# Description of the illustration grant_object_privileges.eps

    { object_privilege | ALL [ PRIVILEGES ] }
      [ (column [, column ]...) ]
        [, { object_privilege | ALL [ PRIVILEGES ] }
           [ (column [, column ]...) ]
        ]...
    on_object_clause
    TO grantee_clause
      [ WITH HIERARCHY OPTION ]
      [ WITH GRANT OPTION ]
