# Description of the illustration reverse_migrate_key.eps

    SET [ ENCRYPTION ] KEY
      IDENTIFIED BY software_keystore_password
      [ FORCE KEYSTORE ]
      REVERSE MIGRATE USING { HSM_auth_string | OKV_password }
      WITH BACKUP [ USING 'backup_identifier']
