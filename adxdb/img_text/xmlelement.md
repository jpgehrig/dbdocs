XMLELEMENT
     ( [ENTITYESCAPING | NOENTITYESCAPING]
       [ {NAME] identifier
         | EVALNAME value_expr
         }
       [, XML_attributes_clause]
       [, value_expr [[AS] c_alias]
          [, value_expr [[AS] c_alias]
          ]
       ]...
     )
