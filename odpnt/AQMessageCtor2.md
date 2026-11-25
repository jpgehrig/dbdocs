This constructor instantiates the `OracleAQMessage` class using the `Object` provided as the `payload`.

### Declaration

    // C#
    public OracleAQMessage(Object payload);

### Parameters

- `payload`

  An `Object` specifying `payload`. It can be one of the following types:

  - `byte[]`

  - `IOracleCustomType`

  - `OracleBinary`

  - `OracleXmlType`

  - `String`

  - `XmlReader`

### Exceptions

`ArgumentException` - The specified `payload` value is of invalid type.

### Remarks

The ODP.NET AQ implementation currently does not support user defined types with LOB attributes. It also does not support other variants of user defined types such as `VARRAY` and nested tables, as Oracle Database AQ does not support them inherently.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQMessage Class](OracleAQMessageClass.md)

- [OracleAQMessage Members](AQMessageMembers.md)
