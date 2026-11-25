# Description of the illustration alter_tablespace_encryption.eps

    ENCRYPTION
      {
      { OFFLINE { [ tablespace_encryption_spec ] ENCRYPT | DECRYPT } }
      | { ONLINE { { [ tablespace_encryption_spec ] { ENCRYPT | REKEY } }
                   | DECRYPT }
                 [ ts_file_name_convert ] }
      | { FINISH { ENCRYPT | REKEY | DECRYPT } [ ts_file_name_convert ] }
      }
