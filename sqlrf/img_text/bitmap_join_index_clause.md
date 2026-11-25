# Description of the illustration bitmap_join_index_clause.eps

    [ schema.]table
       ( [ [ schema. ]table. | t_alias. ]column
         [ ASC | DESC  ]
           [, [ [ schema. ]table. | t_alias. ]column
              [ ASC | DESC ]
           ]...
       )
       FROM [ schema. ]table [ t_alias ]
              [, [ schema. ]table [ t_alias ]
            ]...
       WHERE condition
          [ local_partitioned_index ] index_attributes
