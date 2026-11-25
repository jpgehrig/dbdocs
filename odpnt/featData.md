The `ExecuteReader` method of the `OracleCommand` object returns an `OracleDataReader` object, which is a read-only, forward-only result set.

This section provides the following information about the `OracleDataReader` object:

- Typed OracleDataReader Accessors

- Obtaining LONG and LONG RAW Data

- Obtaining LOB Data

- Controlling the Number of Rows Fetched in One Database Round-Trip

### Typed OracleDataReader Accessors

The `OracleDataReader` class provides two types of typed accessors:

- .NET Type Accessors

- ODP.NET Type Accessors

#### .NET Type Accessors

Table 3-14 lists all the Oracle native database types that ODP.NET supports, and the corresponding .NET types that can represent the Oracle native type. If more than one .NET type can be used to represent an Oracle native type, the first entry is the .NET type that best represents the Oracle native type. The third column indicates the valid typed accessor that can be invoked for an Oracle native type to be obtained as a .NET type. If an invalid typed accessor is used for a column, an `InvalidCastException` is thrown. Oracle native data types depend on the version of the database; therefore, some data types are not available in earlier versions of Oracle Database.

**See Also:**

- "[OracleDataAdapter Class](OracleDataAdapterClass.md)"

- "[OracleDataReader Class](OracleDataReaderClass.md)"

Table 3-14 .NET Type Accessors

| Oracle Native Data Type                  | .NET Type                                                                                                                      | Typed Accessor                                                                                   |
|:-----------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------|
| `BFILE`                                  | `System.Byte[]`                                                                                                                | `GetBytes`                                                                                       |
| `BINARY_DOUBLE`                          | `System.Double`                                                                                                                | `GetDouble`                                                                                      |
| `BINARY_FLOAT`                           | `System.Single`                                                                                                                | `GetFloat`                                                                                       |
| `BLOB`                                   | `System.Byte[]`                                                                                                                | `GetBytes`                                                                                       |
| `CHAR`                                   | `System.String`<br>`System.Char[]`                                                                                             | `GetString`<br>`GetChars`                                                                        |
| `CLOB`                                   | `System.String`<br>`System.Char[]`                                                                                             | `GetString`<br>`GetChars`                                                                        |
| `DATE`                                   | `System.DateTime`                                                                                                              | `GetDateTime`                                                                                    |
| `INTERVAL` `DAY` `TO` `SECOND`           | `System.Timespan`                                                                                                              | `GetTimeSpan`                                                                                    |
| `INTERVAL` `YEAR` `TO` `MONTH`           | `System.Int64`                                                                                                                 | `GetInt64`                                                                                       |
| `LONG`                                   | `System.String`<br>`System.Char[]`                                                                                             | `GetString`<br>`GetChars`                                                                        |
| `LONG RAW`                               | `System.Byte[``]`                                                                                                              | `GetBytes`                                                                                       |
| `NCHAR`                                  | `System.String`<br>`System.Char[]`                                                                                             | `GetString`<br>`GetChars`                                                                        |
| `NCLOB`                                  | `System.String`<br>`System.Char[]`                                                                                             | `GetString`<br>`GetChars`                                                                        |
| `NUMBER`                                 | `System.Decimal`<br>`System.Byte`<br>`System.Int16`<br>`System.Int32`<br>`System.Int64 `<br>`System.Single`<br>`System.Double` | `GetDecimal`<br>`GetByte`<br>`GetInt16`<br>`GetInt32`<br>`GetInt64`<br>`GetFloat`<br>`GetDouble` |
| `NVARCHAR2`                              | `System.String`<br>`System.Char[]`                                                                                             | `GetString`<br>`GetChars`                                                                        |
| `RAW`                                    | `System.Byte[``]`                                                                                                              | `GetBytes`                                                                                       |
| `REF`                                    | `System.String`                                                                                                                | `GetString`                                                                                      |
| `ROWID`                                  | `System.String`<br>`System.Char[]`                                                                                             | `GetString`<br>`GetChars`                                                                        |
| `TIMESTAMP`                              | `System.DateTime`                                                                                                              | `GetDateTime`                                                                                    |
| `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` | `System.DateTime`                                                                                                              | `GetDateTime`                                                                                    |
| `TIMESTAMP` `WITH` `TIME` `ZONE`         | `System.DateTime`                                                                                                              | `GetDateTime`                                                                                    |
| `UROWID`                                 | `System.String`<br>`System.Char[]`                                                                                             | `GetString`<br>`GetChars`                                                                        |
| `VARCHAR2`                               | `System.String`<br>`System.Char[]`                                                                                             | `GetString`<br>`GetChars`                                                                        |
| `XMLType`                                | `System.String`<br>`System.Xml.XmlReader`                                                                                      | `GetString`<br>`GetXmlReader`                                                                    |

Certain methods and properties of the `OracleDataReader` object require ODP.NET to map a `NUMBER` column to a .NET type based on the precision and scale of the column. These members are:

- `Item` property

- `GetFieldType` method

- `GetValue` method

- `GetValues` method

ODP.NET determines the appropriate .NET type by considering the following .NET types in order, and selecting the first .NET type from the list that can represent the entire range of values of the column:

- `System.Byte`

- `System.Int16`

- `System.Int32`

- `System.Int64`

- `System.Single`

- `System.Double`

- `System.Decimal`

If no .NET type exists that can represent the entire range of values of the column, then an attempt is made to represent the column values as a `System.Decimal` type. If the value in the column cannot be represented as `System.Decimal`, then an exception is raised.

For example, consider two columns defined as `NUMBER(4,0)` and `NUMBER(10,2)`. The first .NET types from the previous list that can represent the entire range of values of the columns are `System.Int16` and `System.Double`, respectively. However, consider a column defined as `NUMBER(20,10)`. In this case, there is no .NET type that can represent the entire range of values on the column, so an attempt is made to return values in the column as a `System.Decimal` type. If a value in the column cannot be represented as a `System.Decimal type`, then an exception is raised.

The `Fill` method of the `OracleDataAdapter` class uses the `OracleDataReader` object to populate or refresh a `DataTable` or `DataSet` with .NET types. As a result, the .NET type used to represent a `NUMBER` column in the `DataTable` or `DataSet` also depends on the precision and scale of the column.

**See Also:**

- "[OracleDataReader Class](OracleDataReaderClass.md)"

- "[OracleDataAdapter Class](OracleDataAdapterClass.md)"

- "[Item](DataReaderItemOverloads.md)"

- "[GetFieldType](DataReaderGetFieldType.md)"

- "[GetValues](DataReaderGetValues.md)"

- "[GetValue](DataReaderGetValue.md)"

#### ODP.NET Type Accessors

ODP.NET exposes provider-specific types that natively represent the data types in the database. In some cases, these ODP.NET types provide better performance and functioning than the corresponding .NET types. The ODP.NET types can be obtained from the `OracleDataReader` object by calling their respective typed accessor.

Table 3-15 lists the valid type accessors that ODP.NET uses to obtain ODP.NET types for an Oracle native type.

Table 3-15 ODP.NET Type Accessors

| Oracle Native Data Type                  | ODP.NET Type                                   | Typed Accessor                                                   |
|:-----------------------------------------|:-----------------------------------------------|:-----------------------------------------------------------------|
| `BFILE`                                  | `OracleBFile`                                  | `GetOracleBFile`                                                 |
| `BINARY_DOUBLE`                          | `OracleDecimal`                                | `GetOracleDecimal`                                               |
| `BINARY_FLOAT`                           | `OracleDecimal`                                | `GetOracleDecimal`                                               |
| `BLOB`                                   | `OracleBlob`<br>`OracleBlob`<br>`OracleBinary` | `GetOracleBlob`<br>`GetOracleBlobForUpdate`<br>`GetOracleBinary` |
| `CHAR`                                   | `OracleString`                                 | `GetOracleString`                                                |
| `CLOB`                                   | `OracleClob`<br>`OracleClob`<br>`OracleString` | `GetOracleClob`<br>`GetOracleClobForUpdate`<br>`GetOracleString` |
| `DATE`                                   | `OracleDate`                                   | `GetOracleDate`                                                  |
| `INTERVAL` `DAY` `TO` `SECOND`           | `OracleIntervalDS`                             | `GetOracleIntervalDS`                                            |
| `INTERVAL` `YEAR` `TO` `MONTH`           | `OracleIntervalYM`                             | `GetOracleIntervalYM`                                            |
| `LONG`                                   | `OracleString`                                 | `GetOracleString`                                                |
| `LONG` `RAW`                             | `OracleBinary`                                 | `GetOracleBinary`                                                |
| `NCHAR`                                  | `OracleString`                                 | `GetOracleString`                                                |
| `NCLOB`                                  | `OracleString`                                 | `GetOracleString`                                                |
| `NUMBER`                                 | `OracleDecimal`                                | `GetOracleDecimal`                                               |
| `NVARCHAR2`                              | `OracleString`                                 | `GetOracleString`                                                |
| `RAW`                                    | `OracleBinary`                                 | `GetOracleBinary`                                                |
| `REF`                                    | OracleRef                                      | `GetOracleRef`                                                   |
| `ROWID`                                  | `OracleString`                                 | `GetOracleString`                                                |
| `TIMESTAMP`                              | `OracleTimeStamp`                              | `GetOracleTimeStamp`                                             |
| `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` | `OracleTimeStampLTZ`                           | `GetOracleTimeStampLTZ`                                          |
| `TIMESTAMP` `WITH` `TIME` `ZONE `        | `OracleTimeStampTZ`                            | `GetOracleTimeStampTZ`                                           |
| `UROWID`                                 | `OracleString`                                 | `GetOracleString`                                                |
| `VARCHAR2`                               | `OracleString`                                 | `GetOracleString`                                                |
| `XMLType`                                | `OracleString`<br>`OracleXmlType`              | `GetOracleString`<br>`GetOracleXmlType`                          |

**See Also:**

"[ODP.NET Types Overview](featTypes.md)" for a list of all ODP.NET types

### Obtaining LONG and LONG RAW Data

ODP.NET fetches and caches rows from the database during the `Read` method invocations on the `OracleDataReader` object. The amount of `LONG` and `LONG` `RAW` column data that is retrieved from this operation is determined by `InitialLONGFetchSize`. The different behaviors observed when `InitialLONGFetchSize` is set to `0`, greater than `0`, and `-1` are explained in the following sections.

**Note:**

ODP.NET does not support the `CommandBehavior.SequentialAccess` enumeration value. Therefore, `LONG` and `LONG` `RAW` data can be fetched randomly.

#### Setting InitialLONGFetchSize to Zero or a Value Greater than Zero

The specified amount of `InitialLONGFetchSize` characters or bytes for `LONG` or `LONG` `RAW` column data is retrieved into the cache during the `Read` method invocations on the `OracleDataReader` object.

By default, `InitialLONGFetchSize` is set to 0. In this case, ODP.NET does not fetch any `LONG` or `LONG` `RAW` column data during the `Read` method invocations on the `OracleDataReader` object. The `LONG` or `LONG` `RAW` data is fetched when the typed accessor method is explicitly invoked for the `LONG` or `LONG` `RAW` column, which incurs a database round-trip because no data is cached.

If `InitialLONGFetchSize` is set to a value greater than `0`, that amount of specified data is cached by ODP.NET during the `Read` method invocations on the `OracleDataReader` object. If the application requests an amount of data less than or equal to the `InitialLONGFetchSize` through the typed accessor methods, no database round-trip is incurred. However, an additional database round-trip is required to fetch data beyond `InitialLONGFetchSize`.

To obtain data beyond the `InitialLONGFetchSize` characters or bytes, one of the following must be in the select list:

- Primary key

- `ROWID`

- Unique columns - (defined as a set of columns on which a unique constraint has been defined or a unique index has been created, where at least one of the columns in the set has a `NOT` `NULL` constraint defined on it)

To be able to fetch the entire `LONG` or `LONG` `RAW` data without having a primary key column, a `ROWID`, or unique columns in the select list, set the size of the `InitialLONGFetchSize` property on the `OracleCommand` object to equal or greater than the number of characters or bytes needed to be retrieved.

The `LONG` or `LONG` `RAW` data is returned when the appropriate typed accessor method (`GetChars`, `GetOracleString`, or `GetString` for `LONG` or `GetOracleBinary` or `GetBytes` for `LONG` `RAW`) is called on the `OracleDataReader` object.

#### Setting InitialLONGFetchSize to -1

By setting `InitialLONGFetchSize` to `-1`, it is possible to fetch the entire `LONG` or `LONG` `RAW` data from the database for a select query, without requiring a primary key, `ROWID`, or unique column in the select list.

When `InitialLONGFetchSize` is set to `-1`, the entire `LONG` or `LONG` `RAW` data is retrieved and cached during `Read` method invocations on the `OracleDataReader` object. Calls to `GetString`, `GetOracleString`, `GetChars`, `GetBytes`, or `GetOracleBinary` in the `OracleDataReader` return the entire column data.

### Obtaining LOB Data

ODP.NET fetches and caches rows from the database during the `Read` method invocations on the `OracleDataReader` object. The amount of LOB column data that is retrieved from this operation is determined by `InitialLOBFetchSize`.

The following is a complete list of typed accessor methods that an application can call for the `CLOB` and `BLOB` columns, if `InitialLOBFetchSize` is set to `0`, greater than `0`, or` -1`:

- Methods callable for `BLOB` column

  - `GetBytes`

  - `GetValue`

  - `GetValues`

  - `GetOracleBinary`

  - `GetOracleBlob`

  - `GetOracleBlobForUpdate`

  - `GetOracleValue`

  - `GetOracleValues`

- Methods callable for `CLOB` column

  - `GetChars`

  - `GetString`

  - `GetValue`

  - `GetValues`

  - `GetOracleString`

  - `GetOracleClob`

  - `GetOracleClobForUpdate`

  - `GetOracleValue`

  - `GetOracleValues`

The following sections explain the different behaviors observed when `InitialLOBFetchSize` is set to `0`, greater than `0`, and -1.

#### Setting InitialLOBFetchSize to Zero

By default, the `InitialLOBFetchSize` property is 0. This value dictates to ODP.NET that any LOBs selected will have their client LOB data fetches deferred until after the `OracleDataReader` `Read`, such as when using the an accessor. Each LOB value is retrieved only at the point it is individually accessed.

The advantage of using this retrieval strategy is that it conserves client memory and bandwidth. If the LOBs selected are either very large or not necessary to be immediately consumed by the end user, or both, then the application can perform better if LOBs are retrieved as needed, rather than all at once.

#### Setting InitialLOBFetchSize to a Value Greater than Zero

If `InitialLOBFetchSize` is set to a value greater than `0`, ODP.NET caches LOB data up to `InitialLOBFetchSize` characters or bytes for each LOB selected during the `Read` method invocations on the `OracleDataReader` object. The maximum value is 2,147,483,647 (2GB). If the total size of a selected LOB is less than this number, the entire LOB data will be read.

By pre-fetching all LOB entries in one or more database round trips, applications can perform faster by reducing round trips. This approach is most advantageous when most LOBs are either small in size, or consumed by the end user almost immediately, or both. The down side of a large fetch size is higher memory consumption.

This section discusses the ways to fetch beyond the `InitialLOBFetchSize` characters or bytes that are cached.

The remaining LOB data is returned when a typed accessor is invoked, regardless of the value set to the `InitialLOBFetchSize` property. Primary key, `ROWID`, or unique columns are not required to be in the query select list to obtain data beyond the specified `InitialLOBFetchSize`.

The `GetOracleBlob`, `GetOracleClob`, `GetOracleBlobForUpdate`, and `GetOracleClobForUpdate` methods can now be invoked even if `InitialLOBFetchSize` is greater than `0`.

#### Setting InitialLOBFetchSize to -1

To fetch all LOB data selected during the read operation and not be bound by a set limit per LOB, set `InitialLOBFetchSize` to `-1`. A new default behavior has been introduced for ODP.NET Release 12.1.0.2 and higher when `InitialLobFetchSize` is set to `-1`.

When `LegacyEntireLOBFetch = 0`, which is the default value, the following operations are invoked for a LOB column:

- `OracleDataReader.GetOracleClob()`: returns `OracleClob` object

- `OracleDataReader.GetOracleBlob() `: returns `OracleBlob` object

- `OracleDataReader.GetOracleClobForUpdate()`: returns `OracleClob` object

- `OracleDataReader.GetOracleBlobForUpdate()`: returns `OracleBlob` object

- `OracleDataReader.GetOracleValue()`: returns `OracleClob` object for a CLOB column

- `OracleDataReader.GetOracleValue()`: returns `OracleBlob` object for a BLOB column

- `OracleDataAdapter.Fill()` with `ProviderSpecificTypes=true`: populates `DataTable` with `OracleClob` for a `CLOB` column

- `OracleDataAdapter.Fill() `with `ProviderSpecificTypes=true`: populates `DataTable` with `OracleBlob` for a `BLOB` column

To use the old behavior, set `LegacyEntireLobFetch = 1` in the ODP.NET configuration.

When `LegacyEntireLobFetch = 1` and `InitialLOBFetchSize = -1`, `GetOracleClob`, `GetOracleClobForUpdate`, `GetOracleBlob`, and `GetOracleBlobForUpdate` methods are not supported. The following operations are invoked for a LOB column in this scenario:

- `OracleDataReader.GetOracleClob()`: throws `InvalidCastException()`

- `OracleDataReader.GetOracleBlob()`: throws `InvalidCastException()`

- `OracleDataReader.GetOracleClobForUpdate()`: throws `InvalidCastException()`

- `OracleDataReader.GetOracleBlobForUpdate()`: throws `InvalidCastException()`

- `OracleDataReader.GetOracleValue()`: returns `OracleString` object for a `CLOB` column

- `OracleDataReader.GetOracleValue()`: returns `OracleBinary` object for a `BLOB` column

- `OracleDataAdapter.Fill()` with `ProviderSpecificTypes=true`: populates `DataTable` with `OracleString` for a `CLOB` column

- `OracleDataAdapter.Fill() `with `ProviderSpecificTypes=true`: populates `DataTable` with `OracleBinary` for a `BLOB` column

For releases prior to ODP.NET 12.1.0.2, by setting `InitialLOBFetchSize` to `-1`, it is possible to fetch the entire LOB data from the database for a select query, without requiring a primary key, `ROWID`, or unique column in the select list. When `InitialLOBFetchSize` is set to `-1`, the entire LOB column data is fetched and cached during the `Read` method invocations on the `OracleDataReader` object. Calls to `GetString`, `GetOracleString`, `GetChars`, `GetBytes`, or `GetOracleBinary` in the `OracleDataReader` allow retrieving all data.

##### Methods Supported for InitialLOBFetchSize of -1 and LegacyEntireLobFetch of 1

This section lists supported and not supported methods for the `CLOB` and `BLOB` data types when the `InitialLOBFetchSize` property is set to `-1` and `LegacyEntireLobFetch` property is set to `1`.

Table 3-16 lists supported and not supported methods for the `CLOB` data types.

Table 3-16 Supported OracleDataReader CLOB Methods for InitialLOBFetchSize of -1 and LegacyEntireLobFetch of 1

| OracleDataReader CLOB Methods | Supported |
|:------------------------------|:----------|
| `GetChars`                    | Yes       |
| `GetString`                   | Yes       |
| `GetValue`                    | Yes       |
| `GetValues`                   | Yes       |
| `GetOracleString`             | Yes       |
| `GetOracleValue`              | Yes       |
| `GetOracleValues`             | Yes       |
| `GetOracleClob`               | No        |
| `GetOracleClobForUpdate`      | No        |

Table 3-17 lists supported and not supported methods for the `BLOB` data types.

Table 3-17 Supported OracleDataReader BLOB Methods for InitialLOBFetchSize of -1 and LegacyEntireLobFetch of 1

| OracleDataReader BLOB Methods | Supported |
|:------------------------------|:----------|
| `GetBytes`                    | Yes       |
| `GetValue`                    | Yes       |
| `GetValues`                   | Yes       |
| `GetOracleBinary`             | Yes       |
| `GetOracleValue`              | Yes       |
| `GetOracleValues`             | Yes       |
| `GetOracleBlob`               | No        |
| `GetOracleBlobForUpdate`      | No        |

#### Performance Considerations Related to the InitialLOBFetchSize Property

This section discusses the advantages and disadvantages of the various `InitialLOBFetchSize` property settings in different situations.

An application does not have to choose between performance and `OracleBlob` and `OracleClob` functionality. Setting the `InitialLOBFetchSize` property results in a performance boost and still gives the flexibility to use the `OracleBlob` and `OracleClob` objects.

If the size of the LOB data is unknown or if the LOB data size varies irregularly, then it is better to leave the `InitialLOBFetchSize` property to its default value of `0`. This still gives better performance in most cases.

Setting the `InitialLOBFetchSize` property to a size equal to or greater than the LOB data size for most rows improves performance. It is generally recommended that the `InitialLOBFetchSize` property be set to a value larger than the size of the LOB data for more than 80% of the rows returned by the query. For example, if the size of the LOB data is less than 1 KB in 80% of the rows, and more than 1 MB for 20% of the rows, set the `InitialLOBFetchSize` property to 1 KB.

**See Also:**

- "[LOB Support](featLOBsupp.md)"

- "[InitialLOBFetchSize](CommandInitialLOBFetchSize.md)"

- "[InitialLONGFetchSize](CommandInitialLONGFetchSize.md)"

### Controlling the Number of Rows Fetched in One Database Round-Trip

Application performance depends on the number of rows the application needs to fetch, and the number of database round-trips that are needed to retrieve them.

#### Use of FetchSize

The `FetchSize` property represents the total memory size in bytes that ODP.NET allocates to cache the data fetched from a database round-trip.

The `FetchSize` property can be set on the `OracleCommand,` `OracleDataReader`, or `OracleRefCursor` object, depending on the situation. It controls the fetch size for filling a `DataSet` or `DataTable` using an `OracleDataAdapter`.

If the `FetchSize` property is set on the `OracleCommand` object, then the newly created `OracleDataReader` object inherits the `FetchSize` property of the `OracleCommand` object. This inherited `FetchSize` value can be left as is, or modified to override the inherited value. The `FetchSize` property of the `OracleDataReader` object can be changed before the first `Read` method invocation, which allocates memory specified by the `FetchSize` property. All subsequent fetches from the database use the same cache allocated for that `OracleDataReader` object. Therefore, changing the `FetchSize` value after the first `Read` method invocation has no effect.

#### Fine-Tuning FetchSize

By fine-tuning the `FetchSize` property, applications can control memory usage and the number of rows fetched in one database round-trip for better performance.

For example, if a query returns 100 rows and each row takes 1024 bytes, then setting the `FetchSize` property to 102400 takes just one database round-trip to fetch 100 rows. For the same query, if the `FetchSize` property is set to 10240, it takes 10 database round-trips to retrieve 100 rows. If the application requires all the rows to be fetched from the result set, the first scenario is faster than the second. However, if the application requires just the first 10 rows from the result set, the second scenario can perform better because it fetches only 10 rows, not 100 rows. When the next 10 rows are fetched, then the memory allocated for rows 1-10 is reused for rows 11-20.

The larger the `FetchSize`, the more system memory is used. Developers should not set large fetch sizes if their client systems have limited memory resources.

#### Using the RowSize Property

The `RowSize` property of the `OracleCommand` or `OracleRefCursor` object is populated with the row size (in bytes) after an execution of a `SELECT` statement. The `FetchSize` property can then be set to a value relative to the `RowSize` property by setting it to the result of multiplying the `RowSize` value times the number of rows to fetch for each database round-trip.

For example, setting the `FetchSize` to `RowSize` \* 10 forces the `OracleDataReader` object to fetch exactly 10 rows for each database round-trip. Note that the `RowSize` value does not change due to the data length in each individual column. Instead, the `RowSize` value is determined strictly from the metadata information of the database table(s) that the `SELECT` statement is executed against.

The `RowSize` property can be used to set the `FetchSize` property at design time or at run time, as described in the following sections.

##### Setting FetchSize Value in the Registry

The `HKLM\Software\Oracle\ODP.NET\`` version``\FetchSize` registry entry can be set to specify the default result set fetch size (in bytes) for all applications that use that particular version of ODP.NET or the `FetchSize` attribute in the application configuration or `web.config` file can specify the default value for a given application. By default, the fetch size is 131072 bytes. This value can be overridden programmatically by having the applications set the `FetchSize` property on either the `OracleCommand` or the `OracleDataReader` at run time.

##### Setting FetchSize Value at Design Time

If the row size for a particular `SELECT` statement is already known from a previous execution, the `FetchSize` value of the `OracleCommand` object can be set at design time to the result of multiplying that row size times the number of rows the application wishes to fetch for each database round-trip. The `FetchSize` value set on the `OracleCommand` object is inherited by the `OracleDataReader` object that is created by the `ExecuteReader` method invocation on the `OracleCommand` object. Rather than setting the `FetchSize` value on the `OracleCommand` object, the `FetchSize` value can also be set on the `OracleDataReader` object directly. In either case, the `FetchSize` value is set at design time, without accessing the `RowSize` property value at run time.

##### Setting FetchSize Value at Run Time

Applications that do not know the row size at design time can use the `RowSize` property of the `OracleCommand` object to set the `FetchSize` property of the `OracleDataReader` object. The `RowSize` property provides a dynamic way of setting the `FetchSize` property based on the size of a row.

After an `OracleDataReader` object is obtained by invoking the `ExecuteReader` method on the `OracleCommand` object, the `RowSize` property is populated with the size of the row (in bytes). By using the `RowSize` property, the application can dynamically set the `FetchSize` property of the `OracleDataReader` object to the product of the `RowSize` property value multiplied by the number of rows the application wishes to fetch for each database round-trip. In this scenario, the `FetchSize` property is set by accessing the `RowSize` property at run time.
