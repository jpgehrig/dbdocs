# Description of the illustration group_by_clause.eps

    GROUP BY
       { expr
       | rollup_cube_clause
       | grouping_sets_clause
       }
         [, { expr
            | rollup_cube_clause
            | grouping_sets_clause
            }
         ]...
       [ HAVING condition ]
