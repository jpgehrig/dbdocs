Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../Datum.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

## Uses of Class oracle.sql.Datum

- **Packages that use [Datum](../Datum.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |
  | oracle.sql  | A package of classes that represent java SQL types and Oracle specific SQL types.                 |

- - ### Uses of [Datum](../Datum.md) in [oracle.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) that return [Datum](../Datum.md)**

    | Modifier and Type          | Method and Description                                                                                                                                                                                           |
    |----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Datum`](../Datum.md)     | OracleCallableStatement.[`getOracleObject`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.Datum` object.                                                    |
    | [`Datum`](../Datum.md)     | OracleResultSet.[`getOracleObject`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                                       |
    | [`Datum`](../Datum.md)     | OracleResultSet.[`getOracleObject`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                                       |
    | [`Datum`](../Datum.md)     | OracleCallableStatement.[`getOracleObject`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.Datum` object.                                                    |
    | [`Datum`](../Datum.md)     | OracleResultSet.[`getOracleObject`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension.          |
    | [`Datum`](../Datum.md)     | OracleResultSet.[`getOracleObject`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension.          |
    | [`Datum`](../Datum.md)`[]` | OracleCallableStatement.[`getOraclePlsqlIndexTable`](../../jdbc/OracleCallableStatement.md)`(int paramIndex)`<br>Deprecated. <br>since 18.1 Use java.sql.CallableStatement.getObject(int parameterIndex) method. |
    | [`Datum`](../Datum.md)`[]` | OracleCallableStatement.[`getOraclePlsqlIndexTable`](../../jdbc/OracleCallableStatement.md)`(int paramIndex)`<br>Deprecated. <br>since 18.1 Use java.sql.CallableStatement.getObject(int parameterIndex) method. |

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) with parameters of type [Datum](../Datum.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                      |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OraclePreparedStatement.[`setOracleObject`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`Datum`](../Datum.md)` x)`<br>Binds the designated parameter to a `oracle.sql.Datum` value.                                                                                                       |
    | `void`            | OraclePreparedStatement.[`setOracleObject`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`Datum`](../Datum.md)` x)`<br>Binds the designated parameter to a `oracle.sql.Datum` value.                                                                                                       |
    | `void`            | OracleCallableStatement.[`setOracleObject`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Datum`](../Datum.md)` x)`<br>Sets the designated parameter to an `oracle.sql.Datum`value.           |
    | `void`            | OracleCallableStatement.[`setOracleObject`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Datum`](../Datum.md)` x)`<br>Sets the designated parameter to an `oracle.sql.Datum`value.           |
    | `void`            | OraclePreparedStatement.[`setOracleObjectAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Datum`](../Datum.md)` value)`<br>Sets the designated parameter to an `oracle.sql.Datum`value. |
    | `void`            | OraclePreparedStatement.[`setOracleObjectAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Datum`](../Datum.md)` value)`<br>Sets the designated parameter to an `oracle.sql.Datum`value. |
    | `void`            | OracleResultSet.[`updateOracleObject`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`Datum`](../Datum.md)` value)`<br>Oracle extension.                                                                                                                                                               |
    | `void`            | OracleResultSet.[`updateOracleObject`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`Datum`](../Datum.md)` value)`<br>Oracle extension.                                                                                                                                                               |
    | `void`            | OracleResultSet.[`updateOracleObject`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`Datum`](../Datum.md)` value)`<br>Oracle extension.                                                                  |
    | `void`            | OracleResultSet.[`updateOracleObject`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`Datum`](../Datum.md)` value)`<br>Oracle extension.                                                                  |

  - ### Uses of [Datum](../Datum.md) in [oracle.sql](../package-summary.md)

    **Subclasses of [Datum](../Datum.md) in [oracle.sql](../package-summary.md)**

    | Modifier and Type | Class and Description                                                                                                                                 |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`ARRAY`](../ARRAY.md)<br>Deprecated. <br>Use java.sql.Array interface for declaration instead of using concrete class oracle.sql.ARRAY.              |
    | `class `          | [`BFILE`](../BFILE.md)<br>Deprecated. <br>Use oracle.jdbc.OracleBfile interface for declaration instead of using concrete class oracle.sql.BFILE.     |
    | `class `          | [`BINARY_DOUBLE`](../BINARY_DOUBLE.md)<br>The BINARY_DOUBLE class is a representation of the Oracle BINARY_DOUBLE datatype.                           |
    | `class `          | [`BINARY_FLOAT`](../BINARY_FLOAT.md)<br>The BINARY_FLOAT class is a representation of the Oracle BINARY_FLOAT datatype.                               |
    | `class `          | [`BLOB`](../BLOB.md)<br>Deprecated. <br>Use java.sql.Blob interface for declaration instead of using concrete class oracle.sql.BLOB.                  |
    | `class `          | [`CHAR`](../CHAR.md)<br>The Oracle specific representation of characters.                                                                             |
    | `class `          | [`CLOB`](../CLOB.md)<br>Deprecated. <br>Use java.sql.Clob interface for declaration instead of using concrete class oracle.sql.CLOB.                  |
    | `class `          | [`DATE`](../DATE.md)<br>**DATE Class**                                                                                                                |
    | `class `          | [`DatumWithConnection`](../DatumWithConnection.md)<br>A supper class for some Oracle specific datatypes, such as BFILE, BLOB, etc.                    |
    | `class `          | [`INTERVALDS`](../INTERVALDS.md)<br>**INTERVALDS Class**                                                                                              |
    | `class `          | [`INTERVALYM`](../INTERVALYM.md)<br>**INTERVALYM Class**                                                                                              |
    | `class `          | [`JAVA_STRUCT`](../JAVA_STRUCT.md)<br>A class for structured data type.                                                                               |
    | `class `          | [`NCLOB`](../NCLOB.md)<br>Deprecated. <br>Use java.sql.NClob interface for declaration instead of using concrete class oracle.sql.NCLOB.              |
    | `class `          | [`NUMBER`](../NUMBER.md)<br>**NUMBER Class**                                                                                                          |
    | `class `          | [`OPAQUE`](../OPAQUE.md)<br>Deprecated. <br>Use oracle.jdbc.OracleOpaque interface for declaration instead of using concrete class oracle.sql.OPAQUE. |
    | `class `          | [`RAW`](../RAW.md)<br>The RAW class is a representation of the Oracle RAW datatype.                                                                   |
    | `class `          | [`REF`](../REF.md)<br>Deprecated. <br>Use java.sql.Ref interface for declaration instead of using concrete class oracle.sql.REF.                      |
    | `class `          | [`ROWID`](../ROWID.md)<br>The ROWID class is a representation of the Oracle ROWID datatype.                                                           |
    | `class `          | [`STRUCT`](../STRUCT.md)<br>Deprecated. <br>Use java.sql.Struct interface for declaration instead of using concrete class oracle.sql.STRUCT.          |
    | `class `          | [`TIMESTAMP`](../TIMESTAMP.md)<br>**TIMESTAMP Class**                                                                                                 |
    | `class `          | [`TIMESTAMPLTZ`](../TIMESTAMPLTZ.md)<br>**TIMESTAMPLTZ Class**                                                                                        |
    | `class `          | [`TIMESTAMPTZ`](../TIMESTAMPTZ.md)<br>**TIMESTAMPTZ Class**                                                                                           |

    **Fields in [oracle.sql](../package-summary.md) declared as [Datum](../Datum.md)**

    | Modifier and Type                  | Field and Description               |
    |------------------------------------|-------------------------------------|
    | `protected `[`Datum`](../Datum.md) | Datum.[`targetDatum`](../Datum.md)  |
    | `protected `[`Datum`](../Datum.md) | Datum.[`targetDatum`](../Datum.md)  |

    **Methods in [oracle.sql](../package-summary.md) that return [Datum](../Datum.md)**

    | Modifier and Type          | Method and Description                                                                                                                                                                                                                                                                    |
    |----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Datum`](../Datum.md)     | ANYDATA.[`accessDatum`](../ANYDATA.md)`()`<br>Returns the embedded object.                                                                                                                                                                                                                |
    | [`Datum`](../Datum.md)     | ANYDATA.[`accessDatum`](../ANYDATA.md)`()`<br>Returns the embedded object.                                                                                                                                                                                                                |
    | [`Datum`](../Datum.md)`[]` | ARRAY.[`getDatumArray`](../ARRAY.md)`()`<br>Deprecated. <br>                                                                                                                                                                                                                              |
    | [`Datum`](../Datum.md)`[]` | STRUCT.[`getDatumArray`](../STRUCT.md)`()`<br>Deprecated. <br>                                                                                                                                                                                                                            |
    | [`Datum`](../Datum.md)`[]` | STRUCT.[`getDatumArray`](../STRUCT.md)`()`<br>Deprecated. <br>                                                                                                                                                                                                                            |
    | [`Datum`](../Datum.md)`[]` | ARRAY.[`getDatumArray`](../ARRAY.md)`()`<br>Deprecated. <br>                                                                                                                                                                                                                              |
    | [`Datum`](../Datum.md)`[]` | ARRAY.[`getOracleArray`](../ARRAY.md)`()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                            |
    | [`Datum`](../Datum.md)`[]` | ARRAY.[`getOracleArray`](../ARRAY.md)`()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                            |
    | [`Datum`](../Datum.md)`[]` | ARRAY.[`getOracleArray`](../ARRAY.md)`(long index, int count)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                       |
    | [`Datum`](../Datum.md)`[]` | ARRAY.[`getOracleArray`](../ARRAY.md)`(long index, int count)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                       |
    | [`Datum`](../Datum.md)`[]` | STRUCT.[`getOracleAttributes`](../STRUCT.md)`()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                     |
    | [`Datum`](../Datum.md)`[]` | STRUCT.[`getOracleAttributes`](../STRUCT.md)`()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                     |
    | [`Datum`](../Datum.md)     | ANYDATA.[`toDatum`](../ANYDATA.md)`(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` c)`                                                                                                                                          |
    | [`Datum`](../Datum.md)     | ORAData.[`toDatum`](../ORAData.md)`(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` c)`<br>Extract an oracle.sql.Datum object.                                                                                                   |
    | [`Datum`](../Datum.md)     | TypeDescriptor.[`toDatum`](../TypeDescriptor.md)`(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` c)`                                                                                                                            |
    | [`Datum`](../Datum.md)     | TypeDescriptor.[`toDatum`](../TypeDescriptor.md)`(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` c)`                                                                                                                            |
    | [`Datum`](../Datum.md)     | ORAData.[`toDatum`](../ORAData.md)`(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` c)`<br>Extract an oracle.sql.Datum object.                                                                                                   |
    | [`Datum`](../Datum.md)     | ANYDATA.[`toDatum`](../ANYDATA.md)`(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` c)`                                                                                                                                          |
    | [`Datum`](../Datum.md)     | CustomDatum.[`toDatum`](../CustomDatum.md)`(oracle.jdbc.driver.OracleConnection c)`<br>Called by setOracleObject to extract a Datum.                                                                                                                                                      |
    | [`Datum`](../Datum.md)     | CustomDatum.[`toDatum`](../CustomDatum.md)`(oracle.jdbc.driver.OracleConnection c)`<br>Called by setOracleObject to extract a Datum.                                                                                                                                                      |
    | [`Datum`](../Datum.md)`[]` | StructDescriptor.[`toOracleArray`](../StructDescriptor.md)`(`[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` attributes)`<br>Deprecated. <br>                                                                                                  |
    | [`Datum`](../Datum.md)`[]` | StructDescriptor.[`toOracleArray`](../StructDescriptor.md)`(`[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` attributes)`<br>Deprecated. <br>                                                                                                  |
    | [`Datum`](../Datum.md)`[]` | ArrayDescriptor.[`toOracleArray`](../ArrayDescriptor.md)`(oracle.jdbc.internal.OracleArray s, `[`Datum`](../Datum.md)` sDatum, long beginIdx, int count, boolean keepLocalCopy)`<br>Deprecated. <br>Side Effect: array.datumArray, array.bytes may be modified if 'keepLocalCopy' is true |
    | [`Datum`](../Datum.md)`[]` | ArrayDescriptor.[`toOracleArray`](../ArrayDescriptor.md)`(oracle.jdbc.internal.OracleArray s, `[`Datum`](../Datum.md)` sDatum, long beginIdx, int count, boolean keepLocalCopy)`<br>Deprecated. <br>Side Effect: array.datumArray, array.bytes may be modified if 'keepLocalCopy' is true |

    **Methods in [oracle.sql](../package-summary.md) with parameters of type [Datum](../Datum.md)**

    | Modifier and Type                                                                                    | Method and Description                                                                                                                                                                                                                                                                                                                                                                                  |
    |------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected boolean`                                                                                  | Datum.[`bytesEqual`](../Datum.md)`(`[`Datum`](../Datum.md)` other)`                                                                                                                                                                                                                                                                                                                                     |
    | `protected boolean`                                                                                  | Datum.[`bytesEqual`](../Datum.md)`(`[`Datum`](../Datum.md)` other)`                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`ANYDATA`](../ANYDATA.md)                                                                  | ANYDATA.[`convertDatum`](../ANYDATA.md)`(`[`Datum`](../Datum.md)` datum)`<br>Constructs an ANYDATA instance from any instance of `Datum`.                                                                                                                                                                                                                                                               |
    | `static `[`ANYDATA`](../ANYDATA.md)                                                                  | ANYDATA.[`convertDatum`](../ANYDATA.md)`(`[`Datum`](../Datum.md)` datum)`<br>Constructs an ANYDATA instance from any instance of `Datum`.                                                                                                                                                                                                                                                               |
    | [`CustomDatum`](../CustomDatum.md)                                                                   | CustomDatumFactory.[`create`](../CustomDatumFactory.md)`(`[`Datum`](../Datum.md)` d, int sqlType)`<br>create an Object from SQL Type and return it.                                                                                                                                                                                                                                                     |
    | [`ORAData`](../ORAData.md)                                                                           | ORADataFactory.[`create`](../ORADataFactory.md)`(`[`Datum`](../Datum.md)` d, int sqlType)`<br>Create an ORAData from a oracle.sql.Datum                                                                                                                                                                                                                                                                 |
    | [`ORAData`](../ORAData.md)                                                                           | ORADataFactory.[`create`](../ORADataFactory.md)`(`[`Datum`](../Datum.md)` d, int sqlType)`<br>Create an ORAData from a oracle.sql.Datum                                                                                                                                                                                                                                                                 |
    | [`CustomDatum`](../CustomDatum.md)                                                                   | CustomDatumFactory.[`create`](../CustomDatumFactory.md)`(`[`Datum`](../Datum.md)` d, int sqlType)`<br>create an Object from SQL Type and return it.                                                                                                                                                                                                                                                     |
    | `byte[]`                                                                                             | ArrayDescriptor.[`toBytes`](../ArrayDescriptor.md)`(oracle.jdbc.internal.OracleArray s, `[`Datum`](../Datum.md)` sDatum, boolean keepLocalCopy)`<br>Deprecated. <br>Side Effect: array.datumArray, array.bytes may be modified if 'keepLocalCopy' is true                                                                                                                                               |
    | `byte[]`                                                                                             | ArrayDescriptor.[`toBytes`](../ArrayDescriptor.md)`(oracle.jdbc.internal.OracleArray s, `[`Datum`](../Datum.md)` sDatum, boolean keepLocalCopy)`<br>Deprecated. <br>Side Effect: array.datumArray, array.bytes may be modified if 'keepLocalCopy' is true                                                                                                                                               |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)`[]`  | ArrayDescriptor.[`toJavaArray`](../ArrayDescriptor.md)`(oracle.jdbc.internal.OracleArray s, `[`Datum`](../Datum.md)` sDatum, long beginIdx, int count, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map, boolean keepLocalCopy)`<br>Deprecated. <br>Side Effect: array.datumArray, array.bytes, s.objectArray may be modified if 'keepLocalCopy' is true |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)`[]`  | ArrayDescriptor.[`toJavaArray`](../ArrayDescriptor.md)`(oracle.jdbc.internal.OracleArray s, `[`Datum`](../Datum.md)` sDatum, long beginIdx, int count, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map, boolean keepLocalCopy)`<br>Deprecated. <br>Side Effect: array.datumArray, array.bytes, s.objectArray may be modified if 'keepLocalCopy' is true |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)      | ArrayDescriptor.[`toNumericArray`](../ArrayDescriptor.md)`(oracle.jdbc.internal.OracleArray array, `[`Datum`](../Datum.md)` arrayDatum, long beginIdx, int count, int type, boolean saveLocalCopy)`<br>Deprecated. <br>                                                                                                                                                                                 |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)      | ArrayDescriptor.[`toNumericArray`](../ArrayDescriptor.md)`(oracle.jdbc.internal.OracleArray array, `[`Datum`](../Datum.md)` arrayDatum, long beginIdx, int count, int type, boolean saveLocalCopy)`<br>Deprecated. <br>                                                                                                                                                                                 |
    | [`Datum`](../Datum.md)`[]`                                                                           | ArrayDescriptor.[`toOracleArray`](../ArrayDescriptor.md)`(oracle.jdbc.internal.OracleArray s, `[`Datum`](../Datum.md)` sDatum, long beginIdx, int count, boolean keepLocalCopy)`<br>Deprecated. <br>Side Effect: array.datumArray, array.bytes may be modified if 'keepLocalCopy' is true                                                                                                               |
    | [`Datum`](../Datum.md)`[]`                                                                           | ArrayDescriptor.[`toOracleArray`](../ArrayDescriptor.md)`(oracle.jdbc.internal.OracleArray s, `[`Datum`](../Datum.md)` sDatum, long beginIdx, int count, boolean keepLocalCopy)`<br>Deprecated. <br>Side Effect: array.datumArray, array.bytes may be modified if 'keepLocalCopy' is true                                                                                                               |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true) | ArrayDescriptor.[`toResultSet`](../ArrayDescriptor.md)`(oracle.jdbc.internal.OracleArray array, `[`Datum`](../Datum.md)` arrayDatum, long index, int count, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map, boolean saveLocalCopy)`<br>Deprecated. <br>                                                                                                |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true) | ArrayDescriptor.[`toResultSet`](../ArrayDescriptor.md)`(oracle.jdbc.internal.OracleArray array, `[`Datum`](../Datum.md)` arrayDatum, long index, int count, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map, boolean saveLocalCopy)`<br>Deprecated. <br>                                                                                                |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../Datum.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
