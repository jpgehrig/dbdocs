# Description of the illustration create_view.eps

    CREATE [OR REPLACE] [[NO] FORCE]
      [ EDITIONING | EDITIONABLE [ EDITIONING ] | NONEDITIONABLE ]
      VIEW [ IF NOT EXISTS ][schema.] view
      [ SHARING = { METADATA | DATA | EXTENDED DATA | NONE } ]
      [ ( { alias [ VISIBLE | INVISIBLE ] [ inline_constraint... ]
          | out_of_line_constraint
          }
            [, { alias [ VISIBLE | INVISIBLE ] [ inline_constraint...]
               | out_of_line_constraint
               }
            ]
        )
      | object_view_clause
      | XMLType_view_clause
      ]
      [ DEFAULT COLLATION collation_name ]
      [ BEQUEATH { CURRENT_USER | DEFINER } ]
      [ annotations_clause ]
      AS subquery [ subquery_restriction_clause ]
      [ CONTAINER_MAP | CONTAINERS_DEFAULT ]
