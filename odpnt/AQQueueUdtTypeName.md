This instance property specifies the type name on which the queue and the corresponding queue table is based if the `MessageType` is `OracleAQMessageType.UDT`.

### Declaration

    // C#
    public string UdtTypeName {get; set;}

### Property Value

Specifies the Oracle user-defined type name if the `MessageType` is `OracleAQMessageType.UDT`.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

The `UdtTypeName` property corresponds to the user-defined type name of the payload. This property must always be specified if the payload is a user-defined type. This property need not be set for other payload types.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQQueue Class](OracleAQQueueClass.md)

- [OracleAQQueue Members](AQQueueMembers.md)
