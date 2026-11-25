# Description of the illustration level_clause.eps

    LEVEL level IS
       { level_table.level_column
       | (level_table.level_column
          [, level_table.level_column ]...
         )
       } [ SKIP WHEN NULL ]
