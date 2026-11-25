This property specifies a subset of the connection string used for the transaction running during the last database outage.

### Declaration

    // C#
    public string ConnectionString {get;}

### Property Value

The data source as a string.

### Remarks

This connection string can be useful if the outcome is not known at the time the exception is thrown due to a service that is down. In such a scenario, use the connection string from this property along with the `LogicalTransactionId` to determine the outcome of the logical transaction by invoking the static `GetOutcome()` method, once the database or service is back up.

The string returned by this property will contain only the following attributes: `User Id`, `Proxy user Id` (if not null/empty), `Data Source`, and `Pooling` (which will be set to `false`).

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleLogicalTransaction Class](OracleLogicalTransactionClass.md)

- [OracleLogicalTransaction Members](LogicalTransactionMembers.md)
