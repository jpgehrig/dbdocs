# Description of the illustration object_view_clause.eps

    OF [ schema. ] type_name
    { WITH OBJECT { IDENTIFIER | ID }
      { DEFAULT | ( attribute [, attribute ]... ) }
    | UNDER [ schema. ] superview
    }
    [ ( { out_of_line_constraint
        | attribute { inline_constraint }...
        }  [, { out_of_line_constraint
              | attribute { inline_constraint }...
              }
           ]...
      )
    ]
