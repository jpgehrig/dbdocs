This property specifies the column mappings between the data source and destination table.

### Declaration

    // C#
    public OracleBulkCopyColumnMappingCollection ColumnMappings {get;}

### Property Value

The `OracleBulkCopyColumnMappingCollection` object that defines the column mapping between the source and destination table.

### Remarks

The `ColumnMappings` collection is unnecessary if the data source and the destination table have the same number of columns, and the ordinal position of each source column matches the ordinal position of the corresponding destination column. However, if the column counts differ, or the ordinal positions are not consistent, the `ColumnMappings` collection must be used to ensure that data is copied into the correct columns.

During the execution of a bulk copy operation, this collection can be accessed, but it cannot be changed.

By default, this property specifies an empty collection of column mappings.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)
