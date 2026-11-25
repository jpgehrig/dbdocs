This property specifies whether the payload of a dequeued message is provided as an ODP.NET specific type or a .NET type.

### Declaration

    // C#
    public bool ProviderSpecificType {get;set;}

### Property Value

A `bool.`

### Remarks

The default value of this property is `false`. For a discussion of how this property affects payload type, refer to "[MessageType](AQQueueMessageType.md)" under the `OracleAQQueue` class.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQDequeueOptions Class](OracleAQDequeueOptionsClass.md)

- [OracleAQDequeueOptions Members](AQDequeueOptionsMembers.md)

- "[MessageType](AQQueueMessageType.md)"
