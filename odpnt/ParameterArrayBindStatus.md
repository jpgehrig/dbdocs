This property specifies the input or output status of each element in the `Value` property before or after an Array Bind or PL/SQL Associative Array execution.

### Declaration

    // C#
    public OracleParameterStatus[] ArrayBindStatus { get; set; }

### Property Value

An array of `OracleParameterStatus` enumerated values.

### Exceptions

`ArgumentOutofRangeException` - The `Status` value specified is invalid.

### Remarks

Default = `null`.

`ArrayBindStatus` is used for Array Bind and PL/SQL Associative Array execution only.

Before execution, `ArrayBindStatus` indicates the bind status of each element in the `Value` property. After execution, it contains the execution status of each element in the `Value` property.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)

- "[ArrayBindCount](CommandArrayBindCount.md)"

- "[OracleParameterStatus Enumeration](OracleParameterStatusEnumeration.md)"

- "[Value](ParameterValue.md)" for more information on binding Associative Arrays

- "[ArrayBindSize](ParameterArrayBindSize.md)"
