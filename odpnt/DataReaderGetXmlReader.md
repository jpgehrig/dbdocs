This method returns the contents of an `XMLType` column as an instance of an .NET `XmlTextReader` object.

### Declaration

    // C#
    public XmlReader GetXmlReader(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

A .NET `XmlTextReader`.

### Exceptions

`InvalidCastException` - The accessor method is invalid for this column type or the column value is `NULL`.

### Remarks

`IsDBNull` should be called to check for `NULL` values before calling this method.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
