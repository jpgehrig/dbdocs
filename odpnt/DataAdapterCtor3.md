This constructor creates an instance of an `OracleDataAdapter` class with the provided `OracleConnection` object and the command text for the `SelectCommand`.

### Declaration

    // C#
    public OracleDataAdapter(string selectCommandText, OracleConnection
        selectConnection);

### Parameters

- `selectCommandText`

  The string that is set as the `CommandText` of the `SelectCommand` property of the `OracleDataAdapter`.

- `selectConnection`

  The `OracleConnection` to connect to the Oracle database.

### Remarks

The `OracleDataAdapter` opens and closes the connection, if it is not already open. If the connection is open, it must be explicitly closed.

Initial values are set for the following `OracleDataAdapter` properties as indicated:

- `MissingMappingAction = MissingMappingAction.Passthrough`

- `MissingSchemaAction = MissingSchemaAction.Add`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataAdapter Class](OracleDataAdapterClass.md)

- [OracleDataAdapter Members](DataAdapterMembers.md)
