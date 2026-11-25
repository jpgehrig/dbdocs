This property is a SQL statement or stored procedure that returns single or multiple result sets.

### Declaration

    // C#
    public OracleCommand SelectCommand {get; set;}

### Property Value

An `OracleCommand` used during the `Fill` call to populate the selected rows to the `DataSet`.

### Remarks

Default = `null`

If the `SelectCommand` does not return any rows, no tables are added to the dataset and no exception is raised.

If the `SELECT` statement selects from a `VIEW`, no key information is retrieved when a `FillSchema()` or a `Fill()` with `MissingSchemaAction.AddWithKey` is invoked.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataAdapter Class](OracleDataAdapterClass.md)

- [OracleDataAdapter Members](DataAdapterMembers.md)

- "[OracleDataAdapter Requery Property](featRequery.md)"
