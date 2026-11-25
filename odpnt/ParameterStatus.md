This property indicates the status of the execution related to the data in the `Value` property.

### Declaration

    // C#
    public OracleParameterStatus Status { get; set; }

### Property Value

An `OracleParameterStatus` enumerated value.

### Exceptions

`ArgumentOutOfRangeException` - The `Status` value specified is invalid.

### Remarks

Default = `OracleParameterStatus.Success`

Before execution, this property indicates the bind status related to the `Value` property. After execution, it returns the status of the execution.

`Status` indicates if:

- A `NULL` is fetched from a column.

- Truncation has occurred during the fetch; then `Value` was not big enough to hold the data.

- A `NULL` is to be inserted into a database column; then `Value` is ignored, and a `NULL` is inserted into a database column.

  This property is ignored for Array Bind and PL/SQL Associative Array Bind. Instead, `ArrayBindStatus` property is used.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)

- "[OracleParameterStatus Enumeration](OracleParameterStatusEnumeration.md)"

- "[ArrayBindStatus](ParameterArrayBindStatus.md)"
