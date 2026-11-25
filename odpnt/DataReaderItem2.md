This property gets the .NET `Value` of the column specified by the column name.

### Declaration

    // C#
    public override object this[string columnName] {get;}

### Parameters

- `columnName`

  The name of the column.

### Property Value

The .NET `Value` of the specified column.

### Implements

`IDataRecord`

### Remarks

Default = Not Applicable

A case-sensitive search is made to locate the specified column by its name. If this fails, then a case-insensitive search is made.

In C#, this property is the indexer for this class.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
