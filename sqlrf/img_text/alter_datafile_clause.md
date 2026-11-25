# Description of the illustration alter_datafile_clause.eps

    DATAFILE
       { 'filename' | filenumber }
         [, 'filename' | filenumber ]...
       }
       { ONLINE
       | OFFLINE [ FOR DROP ]
       | RESIZE size_clause
       | autoextend_clause
       | END BACKUP
       | ENCRYPT
       | DECRYPT
       }
