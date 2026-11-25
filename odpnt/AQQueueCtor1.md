This constructor takes a queue name to initialize a queue object.

### Declaration

    // C#
    public OracleAQQueue(string name);

### Parameters

- `name`

  The name of the queue as specified in the database.

### Exceptions

`ArgumentNullException` - The queue name is `null`.

`ArgumentException` - The queue name is empty.

### Remarks

The operation of creating an `OracleAQQueue` object does not involve checking for the existence of the queue in the database.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
