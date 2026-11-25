This constructor creates an instance of an `OracleDataAdapter` class with the provided `OracleCommand` as the `SelectCommand`.

### Declaration

    // C#
    public OracleDataAdapter(OracleCommand selectCommand);

### Parameters

- `selectCommand`

  The `OracleCommand` that is to be set as the `SelectCommand` property.

### Remarks

Initial values are set for the following `OracleDataAdapter` properties as indicated:

- `MissingMappingAction = MissingMappingAction.Passthrough`

- `MissingSchemaAction = MissingSchemaAction.Add`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataAdapter Class](OracleDataAdapterClass.md)

- [OracleDataAdapter Members](DataAdapterMembers.md)
