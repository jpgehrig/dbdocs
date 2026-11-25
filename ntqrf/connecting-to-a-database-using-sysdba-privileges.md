When connecting to the starter database from a remote computer as `SYS`, you must use a different password from the one described in Oracle Database Installation Guide for Microsoft Windows when logging on with `SYSDBA` privileges.

This is because the password file enables database access in this situation and it requires the password `oracle` for this purpose.

**Parent topic:** [Connecting Remotely to the Database](connecting-remotely-to-the-database.md)
