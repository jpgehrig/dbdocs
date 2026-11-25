This instance property specifies the wait time, in seconds, for a message that matches the search criteria.

### Declaration

    // C#
    public int Wait {get;set;}

### Property Value

Any positive `integer` value or 0 or -1.

### Exceptions

`ArgumentOutOfRangeException` - The specified `Wait` value is invalid.

### Remarks

The default value is -1, which implies an infinite wait. The following values are valid:

- Positive integer: Wait time in seconds.

- `-1`: Wait forever.

- `0`: Do not wait.

A value of less than -1 raises an `ArgumentOutOfRangeException`.

This parameter is ignored if messages in the same group are being dequeued.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQDequeueOptions Class](OracleAQDequeueOptionsClass.md)

- [OracleAQDequeueOptions Members](AQDequeueOptionsMembers.md)
