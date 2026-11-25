ODP.NET types represent Oracle native data types and PL/SQL data types as a structure or as a class. ODP.NET type structures follow [value semantics](glossary.md), while ODP.NET type classes follow [reference semantics](glossary.md). ODP.NET types provide safer and more efficient ways of obtaining Oracle native data and PL/SQL data types in a .NET application than .NET types. For example, an `OracleDecimal` structure holds up to 38 digits of precision, while a .NET `Decimal` only holds up to 28.

Table 3-13 lists data types supported by ODP.NET and their corresponding ODP.NET types: data types in the first column refer to both Oracle native data types and PL/SQL data types of that name. Those data types that exist only in PL/SQL are indicated by (PL/SQL only) after the data type name. The entries for the PL/SQL data types also represent the subtypes of the data types, if any. The third column lists the .NET Framework data type that corresponds to the `Value` property of each ODP.NET type.

Table 3-13 Value Property Type of ODP.NET Type

| Oracle Native Data Type or PL/SQL Data Type | ODP.NET Type                   | .NET Framework Data Types |
|:--------------------------------------------|:-------------------------------|:--------------------------|
| `BFILE`                                     | `OracleBFile` class            | `System.Byte[]`           |
| `BINARY_DOUBLE`                             | `OracleDecimal` structure      | `System.Decimal`          |
| `BINARY_FLOAT`                              | `OracleDecimal` structure      | `System.Decimal`          |
| `BINARY_INTEGER` (PL/SQL only)              | `OracleDecimal` structure      | `System.Decimal`          |
| `BLOB`                                      | `OracleBlob` class             | `System.Byte[]`           |
| `BOOLEAN` (PL/SQL only)                     | `OracleBoolean` structure      | `System.Boolean`          |
| `CHAR`                                      | `OracleString` structure       | `System.String`           |
| `CLOB`                                      | `OracleClob` class             | `System.String`           |
| `DATE`                                      | `OracleDate` structure         | `System.DateTime`         |
| `INTERVAL` `DAY` `TO` `SECOND`              | `OracleIntervalDS` structure   | `System.TimeSpan`         |
| `INTERVAL` `YEAR` `TO` `MONTH`              | `OracleIntervalYM` structure   | `System.Int64`            |
| `LONG`                                      | `OracleString` structure       | `System.String`           |
| `LONG` `RAW`                                | `OracleBinary` structure       | `System.Byte[]`           |
| `NCHAR`                                     | `OracleString` structure       | `System.String`           |
| `NCLOB`                                     | `OracleClob` class             | `System.String`           |
| `NUMBER`                                    | `OracleDecimal` structure      | `System.Decimal`          |
| `NVARCHAR2`                                 | `OracleString` structure       | `System.String`           |
| `PLS_INTEGER` (PL/SQL only)                 | `OracleDecimal` Structure      | `System.Decimal`          |
| `RAW`                                       | `OracleBinary` structure       | `System.Byte[]`           |
| `REF`                                       | `OracleRef` class              | `System.String`           |
| `REF` `CURSOR` (PL/SQL only)                | `OracleRefCursor` class        | Not Applicable            |
| `ROWID`                                     | `OracleString` structure       | `System.String`           |
| `TIMESTAMP`                                 | `OracleTimeStamp` structure    | `System.DateTime`         |
| `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE`    | `OracleTimeStampLTZ` structure | `System.DateTime`         |
| `TIMESTAMP` `WITH` `TIME` `ZONE`            | `OracleTimeStampTZ` structure  | `System.DateTime`         |
| `UROWID`                                    | `OracleString` structure       | `System.String`           |
| `VARCHAR2`                                  | `OracleString` structure       | `System.String`           |
| `XMLType`                                   | `OracleXmlType` class          | `System.String`           |
