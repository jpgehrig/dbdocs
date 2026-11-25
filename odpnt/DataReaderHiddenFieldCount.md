This property gets the number of fields in the `OracleDataReader` that are hidden.

### Declaration

    // C#
    public int HiddenFieldcount { get; }

### Property Value

The number of fields in the `OracleDataReader` that are hidden.

### Exceptions

`InvalidOperationException` - The reader is closed.

### Remarks

`OracleDataReader.FieldCount` and `OracleDataReader.VisibleFieldCount` return the visible field count.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)

- "[VisibleFieldCount](DataReaderVisibleFieldCount.md)"

- "[FieldCount](DataReaderFieldCount.md)"
