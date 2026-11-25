For upgraded databases, improve security by using case-sensitive passwords for default user accounts and user accounts.

For greater security, Oracle recommends that you enable case sensitivity in passwords. Case sensitivity increases the security of passwords by requiring that users enter both the correct password string, and the correct case for each character in that string. For example, the password `hPP5620qr` fails if it is entered as `hpp5620QR` or `hPp5620Qr`.

To secure your database, create passwords in a secure fashion. If you have default passwords in your database, then change these passwords. By default, case sensitivity is enforce when you change passwords. Every password should satisfy the Oracle recommended password requirements, including passwords for predefined user accounts.

For new databases created after the upgrade, there are no additional tasks or management requirements.

### Existing Database Requirements and Guidelines for Password Changes

- If the default security settings for Oracle Database 12c release 1 (12.1) and later are in place, then passwords must be at least eight characters, and passwords such as `welcome` and `oracle` are not allowed.

- The `IGNORECASE` parameter is deprecated. Do not use this parameter.

- For existing databases, to take advantage of password case-sensitivity, you must reset the passwords of existing users during the database upgrade procedure. Reset the password for each existing database user with an `ALTER` `USER` statement.

- Query the `PASSWORD_VERSIONS` column of `DBA_USERS` to find the `USERNAME` of accounts that only have the 10G password version, and do not have either the `11G` or the `12C` password version. Reset the password for any account that has only the `10G` password version.

<!-- -->

- [Finding and Resetting User Passwords That Use the 10G Password Version](finding-and-resetting-user-passwords-10g-password-version.md)
  For better security, find and reset passwords for user accounts that use the `10G` password version so that they use later, more secure password versions.

**See Also:**

- [Oracle Database Security Guide](../dbseg/configuring-authentication.md) for more information about password case sensitivity

- [Oracle Database Security Guide](../dbseg/keeping-your-oracle-database-secure.md) for more information about password strength

**Parent topic:** [Recommended and Best Practices to Complete After Upgrading Oracle Database](recommended-and-best-practices-complete-upgrading-oracle-database.md)
