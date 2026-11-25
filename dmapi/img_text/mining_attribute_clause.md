# Description of the illustration mining_attribute_clause.eps

    USING
    { *
    | { [ schema . ] table . *
      | expr [ AS alias ]
      }
        [, { [ schema . ] table . *
           | expr [ AS alias ]
           }
        ]...
    }
