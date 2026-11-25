Oracle database provides a number of pre-defined aggregate functions such as `MAX`, `MIN`, `SUM` for performing operations on a set of records.

These pre-defined aggregate functions can be used only with scalar data. However, you can create your own custom implementations of these functions, or define entirely new aggregate functions, to use with complex data—for example, with multimedia data stored using object types, opaque types, and LOBs.

User-defined aggregate functions are used in SQL DML statements just like the Oracle database built-in aggregates. Once such functions are registered with the server, the database simply invokes the aggregation routines that you supplied instead of the native ones.

User-defined aggregates can be used with scalar data as well. For example, it may be worthwhile to implement special aggregate functions for working with complex statistical data associated with financial or scientific applications.

User-defined aggregates are a feature of the Extensibility Framework. You implement them using `ODCIAggregate` interface routines.

**See Also:**

[Oracle Database Data Cartridge Developer's Guide](../addci/using-user-defined-aggregate-functions.md) for information on using the `ODCIAggregate` interface routines to implement user-defined aggregate functions
