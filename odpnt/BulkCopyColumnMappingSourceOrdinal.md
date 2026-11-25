This property specifies the column ordinal value of the data source that is being mapped.

### Declaration

    // C#
    public int SourceOrdinal {get; set;}

### Property Value

An integer value that represents the source column ordinal of the mapping.

### Exceptions

`IndexOutOfRangeException` - The source ordinal is invalid.

### Remarks

The `SourceOrdinal` and `SourceColumn` properties are mutually exclusive. The last value set takes precedence.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopyColumnMapping Class](OracleBulkCopyColumnMappingClass.md)

- [OracleBulkCopyColumnMapping Members](OracleBulkCopyColumnMappingMembers.md)
