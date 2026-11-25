# Description of the illustration set_key.eps

    SET [ ENCRYPTION ] KEY { mkid:mk | mk }
      [ USING TAG 'tag' ]
      [ USING ALGORITHM 'encrypt_algorithm' ]
      [ FORCE KEYSTORE ]
      IDENTIFIED BY { EXTERNAL STORE | keystore_password }
      WITH BACKUP [ USING 'backup_identifier' ]
      [ CONTAINER = { ALL | CURRENT } ]
