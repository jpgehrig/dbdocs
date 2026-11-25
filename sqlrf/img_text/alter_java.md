# Description of the illustration alter_java.eps

    ALTER JAVA [ IF EXISTS ]
      { SOURCE | CLASS } [ schema. ]object_name
      [ RESOLVER
          ( ( match_string [, ] { schema_name | - } )... )
      ]
      { { COMPILE | RESOLVE }
      | invoker_rights_clause
      }
