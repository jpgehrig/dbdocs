This method starts up the database using the specified startup mode.

### Declaration

    // C#
    public void Startup(OracleDbStartupMode startupMode, string pfile, bool bMountAndOpen);

### Parameters

- `startupMode`

  An `OracleDBStartupMode` enumeration value.

- `pfile`

  The location and name of the client-side parameter file. For example, `"c:\\admin\\init.ora".`

  The name of the parameter file varies depending on the operating system. For example, it can be in mixed case or lowercase, or it can have a logical name or a variation of the name `init.ora`. The default location is usually `ORACLE_HOME``/dbs` or `ORACLE_HOME``\database.`

- `bMountAndOpen`

  A `true/false` value signifying whether the database is to be mounted and opened.

### Exceptions

`OracleException` - The database startup request has failed.

### Remarks

This method starts a database instance in the specified mode using the specified client-side parameter file. After the database is successfully started, and if `bMountAndOpen` input parameter is `true`, this method also executes the `ALTER DATABASE MOUNT` and `ALTER DATABASE OPEN` statements.

If `bMountAndOpen` is `true`, then this method does not throw an exception for cases where the database is already mounted, opened, or started appropriately. If other errors are encountered, then an exception is thrown.

If `bMountAndOpen` is `false`, then the database must be mounted and opened explicitly by the application. For example, if `db` is an instance of the `OracleDatabase` class, then the application invokes the following:

1.  `db.Startup(OracleDBStartupMode.NoRestriction, null, false);`

2.  `db.ExecuteNonQuery("ALTER DATABASE MOUNT");`

3.  `db.ExecuteNonQuery("ALTER DATABASE OPEN");`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDatabase Class](OracleDatabaseClass.md)

- [OracleDatabase Members](DatabaseMembers.md)

- "[OracleDBStartupMode Enumeration](OracleDBStartupModeEnumeration.md)"
