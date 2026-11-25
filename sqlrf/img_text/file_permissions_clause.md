# Description of the illustration file_permissions_clause.eps

    SET PERMISSION { OWNER | GROUP | OTHER }
      = { NONE | READ ONLY | READ WRITE }
      [, { OWNER | GROUP | OTHER | ALL }
        = { NONE | READ ONLY | READ WRITE } ]...
        FOR FILE 'filename' [, 'filename']...
