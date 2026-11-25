This method executes a command specified in the `CommandText` and returns an `OracleDataReader` object, using the specified behavior.

### Declaration

    // C#
    public OracleDataReader ExecuteReader(CommandBehavior behavior);

### Parameters

- `behavior`

  The expected behavior.

### Return Value

An `OracleDataReader`.

### Implements

`IDbCommand`

### Exceptions

`InvalidOperationException` - The command cannot be executed.

### Remarks

A description of the results and the effect on the database of the query command is indicated by the supplied `behavior` that specifies command behavior.

For valid `CommandBehavior` values and for the command behavior of each `CommandBehavior` enumerated type, read the .NET Framework documentation.

When the `CommandType` property is set to `CommandType.StoredProcedure`, the `CommandText` property should be set to the name of the stored procedure. The command executes this stored procedure when `ExecuteReader()` is called.

If the stored procedure returns stored `REF` `CURSOR`s, read the section on `OracleRefCursor`s for more details. See "[OracleRefCursor Class](OracleRefCursorClass.md)".

The value of `100` is used for the `FetchSize`. If `0` is specified, no rows are fetched. For more information, see "[Obtaining LONG and LONG RAW Data](featData.md)".

If the value of the `XmlCommandType` property is set to `OracleXmlCommandType.Insert`, `OracleXmlCommandType.Update`, `OracleXmlCommandType.Delete`, or `OracleXmlCommandType.Query` then the `ExecuteReader` method throws an `InvalidOperationException`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- "[OracleRefCursor Class](OracleRefCursorClass.md)"
