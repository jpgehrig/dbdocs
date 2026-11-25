# Description of the illustration alter_dimension.eps

    ALTER DIMENSION [ schema. ] dimension
      { ADD { level_clause
            | hierarchy_clause
            | attribute_clause
            | extended_attribute_clause
            }
      } ...
      |
      { DROP { LEVEL level [ RESTRICT | CASCADE ]
             | HIERARCHY hierarchy
             | ATTRIBUTE attribute [ LEVEL level [ COLUMN column ] ]...
             }
      } ...
      |
      COMPILE
      ;
