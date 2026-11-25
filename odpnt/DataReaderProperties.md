`OracleDataReader` properties are listed in Table 6-79.

Table 6-79 OracleDataReader Properties

| Property                                                  | Description                                                                                                                |
|:----------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------|
| [Depth](DataReaderDepth.md)                               | Gets a value indicating the depth of nesting for the current row                                                           |
| [FetchSize](DataReaderFetchSize.md)                       | Specifies the size of `OracleDataReader`'s internal cache                                                                  |
| [FieldCount](DataReaderFieldCount.md)                     | Gets the number of columns in the result set                                                                               |
| [HasRows](DataReaderHasRows.md)                           | Indicates whether the `OracleDataReader` has one or more rows                                                              |
| [HiddenFieldCount](DataReaderHiddenFieldCount.md)         | Gets the number of fields in the `OracleDataReader` that are hidden                                                        |
| [IsClosed](DataReaderIsClosed.md)                         | Indicates whether or not the data reader is closed                                                                         |
| [Item](DataReaderItemOverloads.md)                        | Gets the value of the column (Overloaded)                                                                                  |
| [InitialLOBFetchSize](DataReaderInitialLOBFetchSize.md)   | Specifies the amount that the `OracleDataReader` initially fetches for LOB columns                                         |
| [InitialLONGFetchSize](DataReaderInitialLONGFetchSize.md) | Specifies the amount that the `OracleDataReader` initially fetches for `LONG` and `LONG` `RAW` columns                     |
| [RecordsAffected](DataReaderRecordsAffected.md)           | Gets the number of rows changed, inserted, or deleted by execution of the SQL statement                                    |
| [RowSize](DataReaderRowSize.md)                           | Gets the amount of memory the internal cache of the `OracleDataReader` needs to store one row of data                      |
| [UseEdmMapping](DataReaderUseEdmMapping.md)               | Indicates whether or not the `OracleDataReader` utilizes the Entity Data Model mapping configuration when returning values |
| [VisibleFieldCount](DataReaderVisibleFieldCount.md)       | Gets the number of fields in the `OracleDataReader` that are not hidden                                                    |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
