`OracleDataReader` members are listed in the following tables.

### OracleDataReader Static Methods

The `OracleDataReader` static method is listed in Table 6-75.

Table 6-75 OracleDataReader Static Method

| Method   | Description                                 |
|:---------|:--------------------------------------------|
| `Equals` | Inherited from `System.Object` (Overloaded) |

### OracleDataReader Properties

`OracleDataReader` properties are listed in Table 6-76.

Table 6-76 OracleDataReader Properties

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
| [RowSize](DataReaderRowSize.md)                           | Gets the amount of memory the internal cache of the `OracleDataReader` needs to store one row of data.                     |
| [UseEdmMapping](DataReaderUseEdmMapping.md)               | Indicates whether or not the `OracleDataReader` utilizes the Entity Data Model mapping configuration when returning values |
| [VisibleFieldCount](DataReaderVisibleFieldCount.md)       | Gets the number of fields in the `OracleDataReader` that are not hidden                                                    |

### OracleDataReader Public Methods

`OracleDataReader` public methods are listed in Table 6-77.

Table 6-77 OracleDataReader Public Methods

| Public Method                                                             | Description                                                                                                                                 |
|:--------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| [Close](DataReaderClose.md)                                               | Closes the `OracleDataReader`                                                                                                               |
| `CreateObjRef`                                                            | Inherited from `System.MarshalByRefObject`                                                                                                  |
| [Dispose](DataReaderDispose.md)                                           | Releases any resources or memory allocated by the object                                                                                    |
| `Equals`                                                                  | Inherited from `System.Object` (Overloaded)                                                                                                 |
| [GetBoolean](DataReaderGetBoolean.md)                                     | Returns the `bool` value of the specified numeric column                                                                                    |
| [GetByte](DataReaderGetByte.md)                                           | Returns the `byte` value of the specified column                                                                                            |
| [GetBytes](DataReaderGetBytes.md)                                         | Populates the provided byte array with up to the maximum number of bytes, from the specified offset (in bytes) of the column                |
| [GetChar](DataReaderGetChar.md)                                           | Not Supported                                                                                                                               |
| [GetChars](DataReaderGetChars.md)                                         | Populates the provided character array with up to the maximum number of characters, from the specified offset (in characters) of the column |
| [GetData](DataReaderGetData.md)                                           | Not Supported                                                                                                                               |
| [GetDataTypeName](DataReaderGetDataTypeName.md)                           | Returns the ODP.NET type name of the specified column                                                                                       |
| [GetDateTime](DataReaderGetDateTime.md)                                   | Returns the `DateTime` value of the specified column                                                                                        |
| [GetDateTimeOffset](DataReaderGetDateTimeOffset.md)                       | Returns the `DateTimeOffset` value of the specified column                                                                                  |
| [GetDecimal](DataReaderGetDecimal.md)                                     | Returns the `decimal` value of the specified `NUMBER` column                                                                                |
| [GetDouble](DataReaderGetDouble.md)                                       | Returns the `double` value of the specified `NUMBER` column or `BINARY_DOUBLE` column                                                       |
| [GetEnumerator](DataReaderGetEnumerator.md)                               | Returns an `IEnumerator` that can be used to iterate through the collection                                                                 |
| [GetFieldType](DataReaderGetFieldType.md)                                 | Returns the `Type` of the specified column                                                                                                  |
| [GetFloat](DataReaderGetFloat.md)                                         | Returns the `float` value of the specified `NUMBER` column or `BINARY_FLOAT` column                                                         |
| [GetGuid](DataReaderGetGuid.md)                                           | Returns the `Guid` value of the specified binary data column                                                                                |
| `GetHashCode`                                                             | Inherited from `System.Object`                                                                                                              |
| [GetInt16](DataReaderGetInt16.md)                                         | Returns the `Int16` value of the specified `NUMBER` column                                                                                  |
| [GetInt32](DataReaderGetInt32.md)                                         | Returns the `Int32` value of the specified `NUMBER` column                                                                                  |
| [GetInt64](DataReaderGetInt64.md)                                         | Returns the `Int64` value of the specified `NUMBER` column                                                                                  |
| `GetLifetimeService`                                                      | Inherited by `System.MarshalByRefObject`                                                                                                    |
| [GetName](DataReaderGetName.md)                                           | Returns the name of the specified column                                                                                                    |
| [GetOracleBFile](DataReaderGetOracleBFile.md)                             | Returns an `OracleBFile` object of the specified `BFILE` column                                                                             |
| [GetOracleBinary](DataReaderGetOracleBinary.md)                           | Returns an `OracleBinary` structure of the specified column                                                                                 |
| [GetOracleBlob](DataReaderGetOracleBlob.md)                               | Returns an `OracleBlob` object of the specified `BLOB` column                                                                               |
| [GetOracleBlobForUpdate](DataReaderGetOracleBlobForUpdateOverloads.md)    | Returns an updatable `OracleBlob` object of the specified `BLOB` column<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core        |
| [GetOracleClob](DataReaderGetOracleClob.md)                               | Returns an `OracleClob` object of the specified `CLOB` column                                                                               |
| [GetOracleClobForUpdate](DataReaderGetOracleForUpdateOverloads.md)        | Returns an updatable `OracleClob` object of the specified `CLOB` column<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core        |
| [GetOracleDate](DataReaderGetOracleDate.md)                               | Returns an `OracleDate` structure of the specified `DATE` column                                                                            |
| [GetOracleDecimal](DataReaderGetOracleDecimal.md)                         | Returns an `OracleDecimal` structure of the specified `NUMBER` column                                                                       |
| [GetOracleIntervalDS](DataReaderGetOracleIntervalDS.md)                   | Returns an `OracleIntervalDS` structure of the specified `INTERVAL` `DAY` `TO` `SECOND` column                                              |
| [GetOracleIntervalYM](DataReaderGetOracleIntervalYM.md)                   | Returns an `OracleIntervalYM` structure of the specified `INTERVAL` `YEAR` `TO` `MONTH` column                                              |
| [GetOracleRef](DataReaderGetOracleRef.md)                                 | Returns an `OracleRef` object of the specified `REF` column<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core                    |
| [GetOracleString](DataReaderGetOracleString.md)                           | Returns an `OracleString` structure of the specified column                                                                                 |
| [GetOracleTimeStamp](DataReaderGetOracleTimeStamp.md)                     | Returns an `OracleTimeStamp` structure of the Oracle `TimeStamp` column                                                                     |
| [GetOracleTimeStampLTZ](DataReaderGetOracleTimeStampLTZ.md)               | Returns an `OracleTimeStampLTZ` structure of the specified Oracle `TimeStamp` `WITH` `LOCAL` `TIME` `ZONE` column                           |
| [GetOracleTimeStampTZ](DataReaderGetOracleTimeStampTZ.md)                 | Returns an `OracleTimeStampTZ` structure of the specified Oracle `TimeStamp` `WITH` `TIME` `ZONE` column                                    |
| [GetOracleXmlType](DataReaderGetOracleXmlType.md)                         | Returns an `OracleXmlType` object of the specified `XMLType` column                                                                         |
| [GetOracleValue](DataReaderGetOracleValue.md)                             | Returns the specified column value as a ODP.NET type                                                                                        |
| [GetOracleValues](DataReaderGetOracleValues.md)                           | Gets all the column values as ODP.NET types                                                                                                 |
| [GetOrdinal](DataReaderGetOrdinal.md)                                     | Returns the `0`-based ordinal (or index) of the specified column name                                                                       |
| [GetProviderSpecificFieldType](DataReaderGetProviderSpecificFieldType.md) | Returns the provider-specific type of the specified column                                                                                  |
| [GetProviderSpecificValue](DataReaderGetProviderSpecificValue.md)         | Returns an object that represents the underlying provider-specific value of the specified ordinal                                           |
| [GetProviderSpecificValues](DataReaderGetProviderSpecificValues.md)       | Returns an array of objects that represent the underlying provider-specific values                                                          |
| [GetSchemaTable](DataReaderGetSchemaTable.md)                             | Returns a `DataTable` that describes the column metadata of the `OracleDataReader`                                                          |
| [GetString](DataReaderGetString.md)                                       | Returns the string value of the specified column                                                                                            |
| [GetTimeSpan](DataReaderGetTimeSpan.md)                                   | Returns the `TimeSpan` value of the specified `INTERVAL` `DAY` `TO` `SECOND` column                                                         |
| `GetType`                                                                 | Inherited from `System.Object` class                                                                                                        |
| [GetValue](DataReaderGetValue.md)                                         | Returns the column value as a .NET type                                                                                                     |
| [GetValues](DataReaderGetValues.md)                                       | Gets all the column values as .NET types                                                                                                    |
| [GetXmlReader](DataReaderGetXmlReader.md)                                 | Returns the value of an `XMLType` column as an instance of an .NET `XmlTextReader`                                                          |
| [IsDBNull](DataReaderIsDBNull.md)                                         | Indicates whether or not the column value is null                                                                                           |
| [NextResult](DataReaderNextResult.md)                                     | Advances the data reader to the next result set when reading the results                                                                    |
| [Read](DataReaderRead.md)                                                 | Reads the next row in the result set                                                                                                        |
| `ToString`                                                                | Inherited from `System.Object`                                                                                                              |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)
