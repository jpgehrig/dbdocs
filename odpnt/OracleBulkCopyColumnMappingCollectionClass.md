The `OracleBulkCopyColumnMappingCollection` class represents a collection of `OracleBulkCopyColumnMapping` objects that are used to map columns in the data source to columns in a destination table.

### Class Inheritance

`System.Object`

`  System.CollectionBase`

`    System.OracleBulkCopyColumnMappingCollection`

### Declaration

    // C#
    public sealed class OracleBulkCopyColumnMappingCollection : CollectionBase

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Remarks

Column mappings define the mapping between data source and the target table.

It is not necessary to specify column mappings for all the columns in the data source. If a `ColumnMapping` is not specified, then, by default, columns are mapped based on the ordinal position. This succeeds only if the source and destination table schema match. If there is a mismatch, an `InvalidOperationException` is thrown.

All the mappings in a mapping collection must be by name or ordinal position.

**Note:**

Oracle Data Provider for .NET makes one or more round-trips to the database to determine the column name if the mapping is specified by ordinal position. To avoid this performance overhead, specify the mapping by column name.

### Example

// C#

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- OracleBulkCopyColumnMappingCollection Class

- [OracleBulkCopyColumnMappingCollection Members](OracleBulkCopyColumnMappingCollectionMembers.md)

- [OracleBulkCopyColumnMappingCollection Properties](BulkCopyColumnMappingCollectionProperties.md)

- [OracleBulkCopyColumnMappingCollection Public Methods](BulkCopyColumnMappingCollectionPublicMethods.md)
