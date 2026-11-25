This instance property specifies the locking behavior associated with the dequeue operation.

### Declaration

    // C#
    public OracleAQDequeueMode DequeueMode {get;set;}

### Property Value

An `OracleAQDequeueMode` enumerated value.

### Exceptions

`ArgumentOutOfRangeException` - The specified `DequeueMode` value is invalid.

### Remarks

The default value is `OracleAQDequeueMode.Remove`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQDequeueOptions Class](OracleAQDequeueOptionsClass.md)

- [OracleAQDequeueOptions Members](AQDequeueOptionsMembers.md)
