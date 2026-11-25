The `OracleFailoverEventHandler` represents the signature of the method that handles the `OracleConnection.Failover` event.

### Declaration

    // C#
    public delegate FailoverReturnCode OracleFailoverEventHandler(object sender,
        OracleFailoverEventArgs eventArgs);

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

Not supported in a .NET stored procedure

### Parameter

- `sender`

  The source of the event.

- `eventArgs`

  The `OracleFailoverEventArgs` object that contains the event data.

### Return Type

An `int`.

### Remarks

To receive failover notifications, a callback function can be registered as follows:

    ConObj.Failover += new OracleFailoverEventHandler(OnFailover);

The definition of the callback function `OnFailover` can be as follows:

    public FailoverReturnCode OnFailover(object sender, OracleFailoverEventArgs eventArgs)


**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleFailoverEventArgs Class](OracleFailoverEventArgsClass.md)

- [OracleFailoverEventArgs Members](FailoverEventArgsMembers.md)

- "[Failover](ConnectionFailover.md)"
