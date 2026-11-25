This instance property specifies the delivery mode of the message being enqueued.

### Declaration

    // C#
    public OracleAQMessageDeliveryMode DeliveryMode {get;set;}

### Exceptions

`ArgumentOutOfRangeException` - The specified `Visibility` value is invalid.

### Remarks

The valid values can be any of the following enumerated values:

- `OracleAQMessageDeliveryMode.Persistent`

- `OracleAQMessageDeliveryMode.Buffered`

The default is `OracleAQMessageDeliveryMode.Persistent`.

`OracleAQMessageDeliveryMode.PersistentOrBuffered` cannot be set on this property.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQEnqueueOptions Class](OracleAQEnqueueOptionsClass.md)

- [OracleAQEnqueueOptions Members](AQEnqueueOptionsMembers.md)
