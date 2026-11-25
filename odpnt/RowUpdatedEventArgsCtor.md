The `OracleRowUpdatedEventArgs` constructor creates a new `OracleRowUpdatedEventArgs` instance.

### Declaration

    // C#
    public OracleRowUpdatedEventArgs(DataRow row,IDbCommand command,
        StatementType statementType, DataTableMapping tableMapping);

### Parameters

- `row`

  The `DataRow` sent for `Update`.

- `command`

  The `IDbCommand` executed during the `Update`.

- `statementType`

  The `StatementType` Enumeration value indicating the type of SQL statement executed.

- `tableMapping`

  The `DataTableMapping` used for the `Update`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleRowUpdatedEventArgs Class](OracleRowUpdatedEventArgsClass.md)

- [OracleRowUpdatedEventArgs Members](RowUpdatedEventArgsMembers.md)
