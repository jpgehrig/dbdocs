This method starts up the database.

### Declaration

    // C#
    public void Startup();

### Exceptions

`OracleException` - The database startup request has failed.

### Remarks

This method starts a database instance in the `OracleDbStartupMode.Normal` mode using the server-side parameter file (`spfile`). After the database is successfully started, this method also executes the `ALTER DATABASE MOUNT` and `ALTER DATABASE OPEN` statements.

This method does not throw exceptions for cases where the database is already mounted, opened, or started appropriately. If other errors are encountered, then an exception is thrown.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDatabase Class](OracleDatabaseClass.md)

- [OracleDatabase Members](DatabaseMembers.md)

- "[OracleDBStartupMode Enumeration](OracleDBStartupModeEnumeration.md)"
