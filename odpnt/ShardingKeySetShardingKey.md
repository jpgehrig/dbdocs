This instance method enables applications to set a key within the `OracleShardingKey` object.

### Declaration

    // C#
    public void SetShardingKey(OracleDbType type, object key);

### Exceptions

`InvalidArgumentException` – The supplied argument is invalid

### Remarks

This method sets a key within the `OracleShardingKey` object.

Acceptable `OracleDbType` enumeration values are `Byte`, `Decimal`, `Double`, `Int16`, `In32`, `Int64`, `Single`, `Varchar2`, `String`, `Date`, `TimeStamp`, and `Raw`.

This can be called multiple times to construct a composite key.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleShardingKey Class](OracleShardingKeyClass.md)

- [OracleShardingKey Members](OracleShardingKeyMembers.md)
