This constructor creates an instance of an `OracleDataAdapter` class with the provided connection string and the command text for the `SelectCommand`.

### Declaration

    // C#
    public OracleDataAdapter(string selectCommandText, string
       selectConnectionString);

### Parameters

- `selectCommandText`

  The string that is set as the `CommandText` of the `SelectCommand` property of the `OracleDataAdapter`.

- `selectConnectionString`

  The connection string.

### Remarks

Initial values are set for the following `OracleDataAdapter` properties as indicated:

- `MissingMappingAction = MissingMappingAction.Passthrough`

- `MissingSchemaAction = MissingSchemaAction.Add`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataAdapter Class](OracleDataAdapterClass.md)

- [OracleDataAdapter Members](DataAdapterMembers.md)
