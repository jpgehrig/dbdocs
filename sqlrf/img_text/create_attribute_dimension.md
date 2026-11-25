# Description of the illustration create_attribute_dimension.eps

    CREATE [ OR REPLACE ] [ FORCE | NOFORCE ] ATTRIBUTE DIMENSION
      [ IF NOT EXISTS ] [ schema. ] attr_dimension [ SHARING "=" ( METADATA | NONE ) ] [ classification_clause ]... ]
      [ DIMENSION TYPE { STANDARD | TIME } ]
      attr_dim_using_clause
      attributes_clause
      [ attr_dim_level_clause ]...
      [ all_clause ]
