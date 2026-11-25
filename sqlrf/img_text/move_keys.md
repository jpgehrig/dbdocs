# Description of the image move_keys

    MOVE [ENCRYPTION] KEYS
        TO NEW KEYSTORE keystore_location1
        IDENTIFIED BY keystore1_password
        FROM [FORCE] KEYSTORE
        IDENTIFIED BY keystore_password
        [WITH IDENTIFIER IN
          { 'key_identifier' [, 'key_identifier']... | ( subquery ) } ]
        WITH BACKUP [USING 'backup_identifier']
