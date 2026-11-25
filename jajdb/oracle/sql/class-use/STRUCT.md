Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../STRUCT.md)
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

## Uses of Class oracle.sql.STRUCT

- **Packages that use [STRUCT](../STRUCT.md)**

  | Package        | Description                                                                                                                                               |
  |----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc    | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`.                                                         |
  | oracle.jdbc.aq | This package is an Oracle JDBC extension that provides interfaces to access the Advanced Queuing feature of Oracle for enterprise messaging applications. |
  | oracle.sql     | A package of classes that represent java SQL types and Oracle specific SQL types.                                                                         |

- - ### Uses of [STRUCT](../STRUCT.md) in [oracle.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) that return [STRUCT](../STRUCT.md)**

    | Modifier and Type        | Method and Description                                                                                                                                                                            |
    |--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`STRUCT`](../STRUCT.md) | OracleCallableStatement.[`getSTRUCT`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.STRUCT` object.                                          |
    | [`STRUCT`](../STRUCT.md) | OracleResultSet.[`getSTRUCT`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`STRUCT`](../STRUCT.md) | OracleResultSet.[`getSTRUCT`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`STRUCT`](../STRUCT.md) | OracleCallableStatement.[`getSTRUCT`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.STRUCT` object.                                          |
    | [`STRUCT`](../STRUCT.md) | OracleResultSet.[`getSTRUCT`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |
    | [`STRUCT`](../STRUCT.md) | OracleResultSet.[`getSTRUCT`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) with parameters of type [STRUCT](../STRUCT.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                   |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OraclePreparedStatement.[`setSTRUCT`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`STRUCT`](../STRUCT.md)` struct)`<br>Binds the designated parameter to a `oracle.sql.STRUCT` value.                                                                                                  |
    | `void`            | OraclePreparedStatement.[`setSTRUCT`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`STRUCT`](../STRUCT.md)` struct)`<br>Binds the designated parameter to a `oracle.sql.STRUCT` value.                                                                                                  |
    | `void`            | OracleCallableStatement.[`setSTRUCT`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`STRUCT`](../STRUCT.md)` x)`<br>Sets the designated parameter to an `oracle.sql.STRUCT`value.           |
    | `void`            | OracleCallableStatement.[`setSTRUCT`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`STRUCT`](../STRUCT.md)` x)`<br>Sets the designated parameter to an `oracle.sql.STRUCT`value.           |
    | `void`            | OraclePreparedStatement.[`setSTRUCTAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`STRUCT`](../STRUCT.md)` value)`<br>Sets the designated parameter to an `oracle.sql.STRUCT`value. |
    | `void`            | OraclePreparedStatement.[`setSTRUCTAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`STRUCT`](../STRUCT.md)` value)`<br>Sets the designated parameter to an `oracle.sql.STRUCT`value. |
    | `void`            | OracleResultSet.[`updateSTRUCT`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`STRUCT`](../STRUCT.md)` value)`<br>Oracle extension.                                                                                                                                                                |
    | `void`            | OracleResultSet.[`updateSTRUCT`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`STRUCT`](../STRUCT.md)` value)`<br>Oracle extension.                                                                                                                                                                |
    | `void`            | OracleResultSet.[`updateSTRUCT`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`STRUCT`](../STRUCT.md)` value)`<br>Oracle extension.                                                                   |
    | `void`            | OracleResultSet.[`updateSTRUCT`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`STRUCT`](../STRUCT.md)` value)`<br>Oracle extension.                                                                   |

  - ### Uses of [STRUCT](../STRUCT.md) in [oracle.jdbc.aq](../../jdbc/aq/package-summary.md)

    **Methods in [oracle.jdbc.aq](../../jdbc/aq/package-summary.md) that return [STRUCT](../STRUCT.md)**

    | Modifier and Type        | Method and Description                                                                             |
    |--------------------------|----------------------------------------------------------------------------------------------------|
    | [`STRUCT`](../STRUCT.md) | AQMessage.[`getSTRUCTPayload`](../../jdbc/aq/AQMessage.md)`()`<br>Retrieves the payload as an ADT. |
    | [`STRUCT`](../STRUCT.md) | AQMessage.[`getSTRUCTPayload`](../../jdbc/aq/AQMessage.md)`()`<br>Retrieves the payload as an ADT. |

    **Methods in [oracle.jdbc.aq](../../jdbc/aq/package-summary.md) with parameters of type [STRUCT](../STRUCT.md)**

    | Modifier and Type | Method and Description                                                                                             |
    |-------------------|--------------------------------------------------------------------------------------------------------------------|
    | `void`            | AQMessage.[`setPayload`](../../jdbc/aq/AQMessage.md)`(`[`STRUCT`](../STRUCT.md)` payload)`<br>Sets an ADT payload. |
    | `void`            | AQMessage.[`setPayload`](../../jdbc/aq/AQMessage.md)`(`[`STRUCT`](../STRUCT.md)` payload)`<br>Sets an ADT payload. |

  - ### Uses of [STRUCT](../STRUCT.md) in [oracle.sql](../package-summary.md)

    **Subclasses of [STRUCT](../STRUCT.md) in [oracle.sql](../package-summary.md)**

    | Modifier and Type | Class and Description                                                   |
    |-------------------|-------------------------------------------------------------------------|
    | `class `          | [`JAVA_STRUCT`](../JAVA_STRUCT.md)<br>A class for structured data type. |

    **Methods in [oracle.sql](../package-summary.md) that return [STRUCT](../STRUCT.md)**

    | Modifier and Type        | Method and Description                                                |
    |--------------------------|-----------------------------------------------------------------------|
    | [`STRUCT`](../STRUCT.md) | REF.[`getSTRUCT`](../REF.md)`()`<br>Deprecated. <br>Oracle extension. |
    | [`STRUCT`](../STRUCT.md) | REF.[`getSTRUCT`](../REF.md)`()`<br>Deprecated. <br>Oracle extension. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../STRUCT.md)
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
