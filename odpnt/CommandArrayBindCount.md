This property specifies if the array binding feature is to be used and also specifies the number of array elements to be bound in the `OracleParameter` `Value` property.

### Declaration

    // C#
    public int ArrayBindCount {get; set;}

### Property Value

An `int` value that specifies number of array elements to be bound in the `OracleParameter` `Value` property.

### Exceptions

`ArgumentException` - The `ArrayBindCount` value specified is invalid.

### Remarks

Default = 0.

If `ArrayBindCount` is equal to `0`, array binding is not used; otherwise, array binding is used and `OracleParameter` `Value` property is interpreted as an array of values. The value of `ArrayBindCount` must be specified to use the array binding feature.

If neither `DbType` nor `OracleDbType` is set, it is strongly recommended that you set `ArrayBindCount` before setting the `OracleParameter` `Value` property so that inference of `DbType` and `OracleDbType` from `Value` can be correctly done.

Array binding is not used by default.

If the `XmlCommandType` property is set to any value other than `None`, this property is ignored.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- "[Array Binding](featOraCommand.md)"

- "[Value](ParameterValue.md)"
