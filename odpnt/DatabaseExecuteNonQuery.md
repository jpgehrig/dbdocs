This method executes the supplied non-`SELECT` statement against the database.

### Declaration

    // C#
    public void ExecuteNonQuery(string sql);

### Exceptions

`OracleException` - The command execution has failed.

### Remarks

This method is meant for execution of DDL statements such as `ALTER DATABASE` statements to `OPEN` and `MOUNT` the database, for example. This method should not be used to execute `SQL SELECT` statements. This method does not support any parameter binding.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDatabase Class](OracleDatabaseClass.md)

- [OracleDatabase Members](DatabaseMembers.md)
