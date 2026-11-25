# Description of the illustration create_java.eps

    CREATE [ OR REPLACE ] [ AND { RESOLVE | COMPILE } ] [ NOFORCE ]
      JAVA [ IF NOT EXISTS ]{ { SOURCE | RESOURCE } NAMED [ schema. ] primary_name
           | CLASS [ SCHEMA schema ]
           }
      [ SHARING = { METADATA | NONE } ]
      [ invoker_rights_clause ]
      [ RESOLVER ( (match_string [,] { schema_name | - })...) ]
      { USING { BFILE (directory_object_name, server_file_name)
              | { CLOB | BLOB | BFILE } subquery
              | 'key_for_BLOB'
              }
      | AS source_char
      }
