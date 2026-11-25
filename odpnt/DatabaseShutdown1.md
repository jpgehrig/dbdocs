This method shuts down the database.

### Declaration

    // C#
    public void Shutdown();

### Exceptions

`OracleException` - The database shutdown request has failed.

### Remarks

This method shuts down a database instance in the `OracleDBShutdownMode.Default` mode. New connections are refused, and the method waits for the existing connections to end.

**Note:**

As the shutdown is effected using the `OracleDBShutdownMode.Default` mode, the shutdown request may remain pending if there are open connections other than the connection created by the `OracleDatabase` object.

After the connections have closed, the method closes the database, dismounts the database, and shuts down the instance using the `OracleDBShutdownMode.Final` mode.

This method does not throw exceptions for cases where the database has been already closed, dismounted, or shutdown appropriately. If other errors are encountered, then an exception is thrown.

Invoking this method against an Oracle Real Application Clusters (Oracle RAC) database shuts down only that database instance to which the `OracleDatabase` object is connected.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDatabase Class](OracleDatabaseClass.md)

- [OracleDatabase Members](DatabaseMembers.md)

- "[OracleDBShutdownMode Enumeration](OracleDBShutdownModeEnumeration.md)"
