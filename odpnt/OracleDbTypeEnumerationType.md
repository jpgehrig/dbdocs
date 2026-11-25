`OracleDbType` enumerated values are used to explicitly specify the `OracleDbType` of an `OracleParameter`.

Table 6-177 lists all the `OracleDbType` enumeration values with a description of each enumerated value.

Table 6-177 OracleDbType Enumeration Values

| Member Name    | Description                                                                                               |
|:---------------|:----------------------------------------------------------------------------------------------------------|
| `Array`        | Oracle Collection (`VArray` or Nested Table)<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core |
| `BFile`        | Oracle `BFILE` type                                                                                       |
| `BinaryFloat`  | Oracle `BINARY_FLOAT` type                                                                                |
| `BinaryDouble` | Oracle `BINARY_DOUBLE` type                                                                               |
| `Blob`         | Oracle `BLOB` type                                                                                        |
| `Boolean`      | Oracle `BOOLEAN` type                                                                                     |
| `Byte`         | `byte` type                                                                                               |
| `Char`         | Oracle `CHAR` type                                                                                        |
| `Clob`         | Oracle `CLOB` type                                                                                        |
| `Date`         | Oracle `DATE` type                                                                                        |
| `Decimal`      | Oracle `NUMBER` type                                                                                      |
| `Double`       | 8-byte `FLOAT` type                                                                                       |
| `Int16`        | 2-byte `INTEGER` type                                                                                     |
| `Int32`        | 4-byte `INTEGER` type                                                                                     |
| `Int64`        | 8-byte `INTEGER` type                                                                                     |
| `IntervalDS`   | Oracle `INTERVAL DAY TO SECOND` type                                                                      |
| `IntervalYM`   | Oracle `INTERVAL YEAR TO MONTH` type                                                                      |
| `Long`         | Oracle `LONG` type                                                                                        |
| `LongRaw`      | Oracle `LONG` `RAW` type                                                                                  |
| `NChar`        | Oracle `NCHAR` type                                                                                       |
| `NClob`        | Oracle `NCLOB` type                                                                                       |
| `NVarchar2`    | Oracle `NVARCHAR2` type                                                                                   |
| `Object`       | Oracle `Object`<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core                              |
| `Raw`          | Oracle `RAW` type                                                                                         |
| `Ref`          | Oracle `REF`<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core                                 |
| `RefCursor`    | Oracle `REF` `CURSOR` type                                                                                |
| `Single`       | 4-byte `FLOAT` type, supports 6 precisions                                                                |
| `TimeStamp`    | Oracle `TIMESTAMP` type                                                                                   |
| `TimeStampLTZ` | Oracle `TIMESTAMP WITH LOCAL TIME ZONE `type                                                              |
| `TimeStampTZ`  | Oracle `TIMESTAMP WITH TIME ZONE` type                                                                    |
| `Varchar2`     | Oracle `VARCHAR2` type                                                                                    |
| `XmlType`      | Oracle `XMLType` type                                                                                     |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.5, 4.6, 4.7              | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- "[OracleParameter Class](OracleParameterClass.md)"

- "[OracleParameterCollection Class](OracleParameterCollectionClass.md)"

- `OracleParameter` "[OracleDbType](ParameterOracleDbType.md)"
