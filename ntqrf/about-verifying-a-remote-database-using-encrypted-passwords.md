Learn how to verify a remote database using encrypted passwords.

With Oracle Database, the password used to verify a remote database connection is automatically encrypted. Whenever a user attempts a remote login, Oracle Database encrypts the password before sending it to the remote database. If the connection fails, then the failure is noted in the operating system audit log.

**Note:**

The configuration parameter `ORA_ENCRYPT_LOGIN` is retained for backward compatibility and is set to `true` by default.

**Related Topics**

- [Configuration Parameters and the Registry](configuration-parameters-and-registry.md)

**Parent topic:** [Connecting Remotely to the Database](connecting-remotely-to-the-database.md)
