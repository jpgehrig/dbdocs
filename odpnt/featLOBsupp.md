ODP.NET provides an easy and optimal way to access and manipulate large object (LOB) data types.

**Note:**

SecureFiles can be used with existing ODP.NET LOB classes.

This section includes the following topics:

- Large Character and Large Binary Data Types

- Oracle Data Provider for .NET LOB Objects

- Updating LOBs Using a DataSet

- Updating LOBs Using OracleCommand and OracleParameter

- Updating LOBs Using ODP.NET LOB Objects

- Temporary LOBs

### Large Character and Large Binary Data Types

Oracle Database supports large character and large binary data types.

#### Large Character Data Types

- `CLOB` - Character data can store up to 4 gigabytes.

- `NCLOB` - Unicode National character set data can store up to 4 gigabytes.

#### Large Binary Data Types

- `BLOB` - Unstructured binary data can store up to 4 gigabytes.

- `BFILE` - Binary data stored in external file can store up to 4 gigabytes.

  **Note:**

  `LONG` and `LONG` `RAW` data types are made available for backward compatibility in Oracle9i, but should not be used in new applications.

### Oracle Data Provider for .NET LOB Objects

ODP.NET provides three objects for manipulating LOB data: `OracleBFile`, `OracleBlob`, and `OracleClob`.

Table 3-19 shows the proper ODP.NET object to use for a particular Oracle LOB type.

Table 3-19 ODP.NET LOB Objects

| Oracle LOB Type | ODP.NET LOB Object |
|:----------------|:-------------------|
| `BFILE`         | `OracleBFile`      |
| `BLOB`          | `OracleBlob`       |
| `CLOB`          | `OracleClob`       |
| `NCLOB`         | `OracleClob`       |

The ODP.NET LOB objects can be obtained by calling the proper typed accessor on the `OracleDataReader` object, or by calling the proper typed accessor as an output parameter on a command execution with the proper bind type.

All ODP.NET LOB objects inherit from the .NET `Stream` class to provide generic `Stream` operations. The LOB data (except for `BFILE` types) can be updated using the ODP.NET LOB objects by using methods such as `Write`. Data is not cached in the LOB objects when read and write operations are carried out. Therefore, each read or write request incurs a database round-trip. The `OracleClob` object overloads the `Read` method, providing two ways to read data from a `CLOB`. The `Read` method that takes a `byte[]` as the buffer populates it with `CLOB` data as Unicode byte array. The `Read` method that takes a `char[]` as the buffer populates it with Unicode characters.

Additional methods can also be found on the `OracleBFile` object. An `OracleBFile` object must be explicitly opened using the `OpenFile` method before any data can be read from it. To close a previously opened `BFILE`, use the `CloseFile` method.

Every ODP.NET LOB object is a connected object and requires a connection during its lifetime. If the connection associated with a LOB object is closed, then the LOB object is not usable and should be disposed of.

If an ODP.NET LOB object is obtained from an `OracleDataReader` object through a typed accessor, then its `Connection` property is set with a reference to the same `OracleConnection` object used by the `OracleDataReader` object. If a LOB object is obtained as an output parameter, then its `Connection` property is set with a reference to the same `OracleConnection` property used by the `OracleCommand` object. If a LOB object is obtained by invoking an ODP.NET LOB object constructor to create a temporary LOB, the `Connection` property is set with a reference to the `OracleConnection` object provided in the constructor.

The ODP.NET LOB object `Connection` property is read-only and cannot be changed during its lifetime. In addition, the ODP.NET LOB types object can be used only within the context of the same `OracleConnection` referenced by the ODP.NET LOB object. For example, the ODP.NET LOB `Connection` property must reference the same connection as the `OracleCommand` object if the ODP.NET LOB object is a parameter of the `OracleCommand`. If that is not the case, ODP.NET raises an exception when the command is executed.

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/introduction-to-large-objects.md)for complete information about Oracle Database 10g LOBs and how to use them

### Updating LOBs Using a DataSet

`BFILE` and `BLOB` data are stored in the `DataSet` as `byte` arrays while `CLOB` and `NCLOB` data are stored as `string`s. In a similar manner to other types, an `OracleDataAdapter` object can be used to fill and update LOB data changes along with the use of the `OracleCommandBuilder` object for automatically generating SQL.

Note that an Oracle LOB column can store up to 4 GB of data. When the LOB data is fetched into the `DataSet`, the actual amount of LOB data the `DataSet` can hold for a LOB column is limited to the maximum size of a .NET string type, which is 2 GB. Therefore, when fetching LOB data that is greater than 2 GB, ODP.NET LOB objects must be used to avoid any data loss.

### Updating LOBs Using OracleCommand and OracleParameter

To update LOB columns, LOB data can be bound as a parameter for SQL statements, anonymous PL/SQL blocks, or stored procedures. The parameter value can be set as a NET Framework type, ODP.NET type, or as an ODP.NET LOB object type. For example, when inserting .NET string data into a LOB column in an Oracle9i database or later, that parameter can be bound as `OracleDbType.Varchar2`. For a parameter whose value is set to an `OracleClob` object, the parameter should be bound as `OracleDbType.Clob`.

### Updating LOBs Using ODP.NET LOB Objects

Oracle `BFILE`s cannot be updated; therefore, `OracleBFile` objects do not allow updates to `BFILE` columns.

Two requirements must be met to update LOB data using ODP.NET LOB objects:

1.  A transaction must be started before a LOB column is selected.

    The transaction must be started using the `BeginTransaction` method on the `OracleConnection` object before the command execution, so that the lock can be released when the `OracleTransaction` `Commit` or `Rollback` method is invoked.

2.  The row in which the LOB column resides must be locked; as part of an entire result set, or on a row-by-row basis.

    1.  Locking the entire result set

        Add the `FOR` `UPDATE` clause to the end of the `SELECT` statement. After execution of the command, the entire result set is locked.

    2.  Locking the row - there are two options:

        - Invoke one of the `OracleDataReader` typed accessors (`GetOracleClobForUpdate` or `GetOracleBlobForUpdate`) on the `OracleDataReader` object to obtain an ODP.NET LOB object, while also locking the current row.

          This approach requires a primary key, unique column(s), or a `ROWID` in the result set because the `OracleDataReader` object must uniquely identify the row to re-select it for locking.

        - Execute an `INSERT` or an `UPDATE` statement that returns a LOB in the `RETURNING` clause.

### Temporary LOBs

Temporary LOBs can be instantiated for `BLOB`, `CLOB`, and `NCLOB` objects. To instantiate an ODP.NET LOB object that represents a temporary LOB, the `OracleClob` or the `OracleBlob` constructor can be used.

Temporary ODP.NET LOB objects can be used for the following purposes:

- To initialize and populate a LOB column with empty or non-empty LOB data.

- To pass a LOB type as an input parameter to a SQL statement, an anonymous PL/SQL block, or a stored procedure.

- To act as the source or the destination of data transfer between two LOB objects as in the `CopyTo` operation.

  **Note:**

  Temporary LOBs are not transaction aware. Commit and rollback operations do not affect the data referenced by a temporary LOB.
