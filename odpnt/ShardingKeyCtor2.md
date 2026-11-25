This constructor enables applications to construct the `OracleShardingKey` object with the supplied key.

### Declaration

    // C#
    public OracleShardingKey(OracleDbType type, object key);

### Exceptions

`InvalidArgumentException` – The supplied argument is invalid

### Remarks

This constructs an `OracleShardingKey` with the supplied key set.

Acceptable `OracleDbType` enumeration values are `Byte`, `Decimal`, `Double`, `Int16`, `In32`, `Int64`, `Single`, `Varchar2`, `String`, `Date`, `TimeStamp`, and `Raw`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleShardingKey Class](OracleShardingKeyClass.md)

- [OracleShardingKey Members](OracleShardingKeyMembers.md)
