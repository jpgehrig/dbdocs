# Description of the illustration storage_clause.eps

    STORAGE
    ({ INITIAL size_clause
     | NEXT size_clause
     | MINEXTENTS integer
     | MAXEXTENTS { integer | UNLIMITED }
     | maxsize_clause
     | PCTINCREASE integer
     | FREELISTS integer
     | FREELIST GROUPS integer
     | OPTIMAL [ size_clause | NULL ]
     | BUFFER_POOL { KEEP | RECYCLE | DEFAULT }
     | FLASH_CACHE { KEEP | NONE | DEFAULT }
      | ( CELL_FLASH_CACHE ( KEEP | NONE | DEFAULT ) )
     | ENCRYPT
     } ...
    )
