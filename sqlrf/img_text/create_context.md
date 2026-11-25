# Description of the illustration create_context.eps

    CREATE [ OR REPLACE ] CONTEXT namespace
      USING [ schema. ] package
      [ SHARING "=" ( METADATA | NONE ) ]
      [ INITIALIZED { EXTERNALLY | GLOBALLY }
      | ACCESSED GLOBALLY
      ] ;
