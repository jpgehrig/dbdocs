The logical transaction id is used to determine the commit outcome of the last transaction open in a database session following an outage.

### Declaration

    // C#
    public byte LogicalTransactionId {get;}

### Property Value

byte\[\]

### Remarks

This logical transaction id can be useful if the outcome is not known at the time the exception is thrown due to a service that is down. In such a scenario, use the `byte[]` returned from this property (along with the `ConnectionString`) to determine the outcome of the logical transaction by invoking the static `GetOutcome()` method, once the database or service is back up.

This property will return a non-null value only when the outcome is not known. For example when database or service is down, then the outcome is not known.

`LogicalTransactionId` property will return `null` if the connection has participated in a distributed transaction.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleLogicalTransaction Class](OracleLogicalTransactionClass.md)

- [OracleLogicalTransaction Members](LogicalTransactionMembers.md)
