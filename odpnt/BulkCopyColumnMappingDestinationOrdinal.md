This property specifies the column ordinal value of the destination table that is being mapped.

### Declaration

    // C#
    public int DestinationOrdinal {get; set;}

### Property Value

An integer value that represents the destination column ordinal of the mapping.

### Exceptions

`IndexOutOfRangeException` - The destination ordinal is invalid.

### Remarks

The `DestinationOrdinal` and `DestinationColumn` properties are mutually exclusive. The last value set takes precedence.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopyColumnMapping Class](OracleBulkCopyColumnMappingClass.md)

- [OracleBulkCopyColumnMapping Members](OracleBulkCopyColumnMappingMembers.md)
