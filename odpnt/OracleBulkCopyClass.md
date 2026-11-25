An `OracleBulkCopy` object efficiently bulk loads or copies data into an Oracle table from another data source.

### Class Inheritance

`System.Object`

`  System.OracleBulkCopy`

### Declaration

    // C#
    public sealed class OracleBulkCopy : IDisposable


### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Remarks

The `OracleBulkCopy` class can be used to write data to Oracle database tables only. However, the data source is not limited to Oracle databases; any data source can be used, as long as the data can be loaded to a `DataTable` instance or read with an `IDataReader` instance.

Bulk copy of string data to destination number column is currently not supported.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)

- [OracleBulkCopy Constructors](BulkCopyConstructors.md)

- [OracleBulkCopy Properties](BulkCopyProperties.md)

- [OracleBulkCopy Public Methods](BulkCopyPublicMethods.md)

- [OracleBulkCopy Events](BulkCopyEvents.md)
