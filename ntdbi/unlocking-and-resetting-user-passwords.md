## Unlocking and Resetting User Passwords

Passwords for all Oracle system administration accounts except `SYS`, `SYSTEM`, and `DBSNMP` are revoked after installation.

Before you use a locked account, you must unlock it and reset its password. If you created a preconfigured database during the installation, but you did not unlock accounts required to use the database, then you must unlock and reset those accounts using these procedures.

Apply the following guidelines when specifying passwords:

- Passwords must be between 8 and 30 characters long.

- Passwords must not start with a numeral.

- Password cannot contain invalid characters: ! @ % ^ & \* ( ) + = \\ \| \` ~ \[ { \] } ; : ' " , \< \> ?

- Passwords must not be the same as the user name.

- Passwords must not be Oracle reserved words.

- The `SYSTEM` account password cannot be `manager`

  (case-insensitive).

- The `SYSMAN` account password cannot be `sysman`

  (case-insensitive).

- The `DBSNMP` account password cannot be `dbsnmp`

  (case-insensitive).

- If you choose to use the same password for all the accounts, then that password cannot be `manager`, `sysman`, or `dbsnmp`

  (case-insensitive).

- Passwords must have at least one alphabetic, one numeric, and one special character.

- Passwords must not be simple or obvious words, such as `welcome`, `account`, `database`, and `user`.

**Note:**

If you select the option to create the database as a multitenant container database, then you must provide the pluggable database administrator password.

If you created a starter database during the installation, but you did not unlock the required account, unlock the account using one of the following methods:

**See Also:**

[Oracle Database Administrator's Guide](../admin/index.md)

**Parent topic:** [Reviewing User Accounts and Passwords](reviewing-user-accounts-and-passwords.md)
