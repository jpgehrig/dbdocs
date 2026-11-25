`OracleParameter` properties are listed in Table 6-127.

Table 6-127 OracleParameter Properties

| Property                                                       | Description                                                                                                                                                                                                         |
|:---------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [ArrayBindSize](ParameterArrayBindSize.md)                     | Specifies the input or output size of elements in `Value` property of a parameter before or after an Array Bind or PL/SQL Associative Array Bind execution                                                          |
| [ArrayBindStatus](ParameterArrayBindStatus.md)                 | Specifies the input or output status of elements in `Value` property of a parameter before or after an Array Bind or PL/SQL Associative Array Bind execution                                                        |
| [CollectionType](ParameterCollectionType.md)                   | Specifies whether or not the `OracleParameter` represents a collection, and if so, specifies the collection type                                                                                                    |
| [DbType](ParameterDbtype.md)                                   | Specifies the data type of the parameter using the `Data.DbType` enumeration type                                                                                                                                   |
| [Direction](ParameterDirection.md)                             | Specifies whether the parameter is input-only, output-only, bi-directional, or a stored function return value parameter                                                                                             |
| [IsNullable](ParameterIsNullable.md)                           | Not supported                                                                                                                                                                                                       |
| [Offset](ParameterOffset.md)                                   | Specifies the offset to the `Value` property or offset to the elements in the `Value` property                                                                                                                      |
| [OracleDbType](ParameterOracleDbType.md)                       | Specifies the Oracle data type                                                                                                                                                                                      |
| [OracleDbTypeEx](ParameterOracleDbTypeEx.md)                   | Specifies the Oracle data type to bind the parameter as, but returns a .NET type as output                                                                                                                          |
| [ParameterName](ParameterParameterName.md)                     | Specifies the name of the parameter                                                                                                                                                                                 |
| [Precision](ParameterPrecision.md)                             | Specifies the maximum number of digits used to represent the `Value` property                                                                                                                                       |
| [Scale](ParameterScale.md)                                     | Specifies the number of decimal places to which `Value` property is resolved                                                                                                                                        |
| [Size](ParameterSize.md)                                       | Specifies the maximum size, in bytes or characters, of the data transmitted to or from the database. For PL/SQL Associative Array Bind, `Size` specifies the maximum number of elements in PL/SQL Associative Array |
| [SourceColumn](ParameterSourceColumn.md)                       | Specifies the name of the `DataTable` Column of the `DataSet`                                                                                                                                                       |
| [SourceColumnNullMapping](ParameterSourceColumnNullMapping.md) | Specifies a value which indicates whether the source column is nullable                                                                                                                                             |
| [SourceVersion](ParameterSourceVersion.md)                     | Specifies the `DataRowVersion` value to use when loading the `Value` property of the parameter                                                                                                                      |
| [Status](ParameterStatus.md)                                   | Indicates the status of the execution related to the data in the `Value` property                                                                                                                                   |
| [UdtTypeName](ParameterUdtTypeName.md)                         | Specifies the Oracle user-defined type name if the parameter is a user-defined data type                                                                                                                            |
| [Value](ParameterValue.md)                                     | Specifies the value of the `Parameter`                                                                                                                                                                              |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)
