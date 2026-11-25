# Description of the illustration attr_dim_level_clause.eps

    LEVEL level [ { NOT NULL  |  SKIP WHEN NULL } ]
      [ classification_clause [ classification_clause ]...
      [ LEVEL TYPE
          {   STANDARD
            | YEARS
            | HALF_YEARS
            | QUARTERS
            | MONTHS
            | WEEKS
            | DAYS
            | HOURS
            | MINUTES
            | SECONDS
          }
      ]
      key_clause [ alternate_key_clause ]
      [ MEMBER NAME expression ]
      [ MEMBER CAPTION expression ]
      [ MEMBER DESCRIPTION expression ]
      [ ORDER BY  [ MIN | MAX ] dim_order_clause
                        [, [ MIN | MAX ] dim_order_clause ]... ]
      ]
      [ DETERMINES ( attribute [, attribute]... ) ]
