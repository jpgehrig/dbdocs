The `OracleRowUpdatingEventArgs` constructor creates a new instance of the `OracleRowUpdatingEventArgs` class using the supplied data row, `IDbCommand`, type of SQL statement, and table mapping.

### Declaration

    // C#
    public OracleRowUpdatingEventArgs(DataRow row, IDbCommand command,
        StatementType statementType, DataTableMapping tableMapping);

### Parameters

- `row`

  The `DataRow` sent for `Update`.

- `command`

  The `IDbCommand` executed during the `Update`.

- `statementType`

  The `StatementType` enumeration value indicating the type of SQL statement executed.

- `tableMapping`

  The `DataTableMapping` used for the `Update`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleRowUpdatingEventArgs Class](OracleRowUpdatingEventArgsClass.md)

- [OracleRowUpdatingEventArgs Members](OracleRowUpdatingEventArgsmembers.md)
