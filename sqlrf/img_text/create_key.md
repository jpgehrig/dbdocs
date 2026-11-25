# Description of the illustration create_key.eps

    CREATE [ ENCRYPTION ] KEY
      [ USING TAG 'tag' ]
      [ USING ALGORITHM 'encrypt_algorithm' ]
      [ FORCE KEYSTORE ]
      IDENTIFIED BY { EXTERNAL STORE | keystore_password }
      WITH BACKUP [ USING 'backup_identifier' ]
      [ CONTAINER = { ALL | CURRENT } ]
