Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../RAW.md)
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

## Uses of Class oracle.sql.RAW

- **Packages that use [RAW](../RAW.md)**

  | Package        | Description                                                                                                                                               |
  |----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc    | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`.                                                         |
  | oracle.jdbc.aq | This package is an Oracle JDBC extension that provides interfaces to access the Advanced Queuing feature of Oracle for enterprise messaging applications. |
  | oracle.sql     | A package of classes that represent java SQL types and Oracle specific SQL types.                                                                         |

- - ### Uses of [RAW](../RAW.md) in [oracle.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) that return [RAW](../RAW.md)**

    | Modifier and Type  | Method and Description                                                                                                                                                                         |
    |--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`RAW`](../RAW.md) | OracleCallableStatement.[`getRAW`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.RAW` object.                                             |
    | [`RAW`](../RAW.md) | OracleResultSet.[`getRAW`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`RAW`](../RAW.md) | OracleResultSet.[`getRAW`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`RAW`](../RAW.md) | OracleCallableStatement.[`getRAW`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.RAW` object.                                             |
    | [`RAW`](../RAW.md) | OracleResultSet.[`getRAW`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |
    | [`RAW`](../RAW.md) | OracleResultSet.[`getRAW`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) with parameters of type [RAW](../RAW.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                       |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OraclePreparedStatement.[`setRAW`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`RAW`](../RAW.md)` raw)`<br>Binds the designated parameter to a `oracle.sql.RAW` value.                                                                                                     |
    | `void`            | OraclePreparedStatement.[`setRAW`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`RAW`](../RAW.md)` raw)`<br>Binds the designated parameter to a `oracle.sql.RAW` value.                                                                                                     |
    | `void`            | OracleCallableStatement.[`setRAW`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`RAW`](../RAW.md)` x)`<br>Sets the designated parameter to an `oracle.sql.RAW`value.           |
    | `void`            | OracleCallableStatement.[`setRAW`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`RAW`](../RAW.md)` x)`<br>Sets the designated parameter to an `oracle.sql.RAW`value.           |
    | `void`            | OraclePreparedStatement.[`setRAWAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`RAW`](../RAW.md)` value)`<br>Sets the designated parameter to an `oracle.sql.RAW`value. |
    | `void`            | OraclePreparedStatement.[`setRAWAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`RAW`](../RAW.md)` value)`<br>Sets the designated parameter to an `oracle.sql.RAW`value. |
    | `void`            | OracleResultSet.[`updateRAW`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`RAW`](../RAW.md)` value)`<br>Oracle extension.                                                                                                                                                             |
    | `void`            | OracleResultSet.[`updateRAW`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`RAW`](../RAW.md)` value)`<br>Oracle extension.                                                                                                                                                             |
    | `void`            | OracleResultSet.[`updateRAW`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`RAW`](../RAW.md)` value)`<br>Oracle extension.                                                                |
    | `void`            | OracleResultSet.[`updateRAW`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`RAW`](../RAW.md)` value)`<br>Oracle extension.                                                                |

  - ### Uses of [RAW](../RAW.md) in [oracle.jdbc.aq](../../jdbc/aq/package-summary.md)

    **Methods in [oracle.jdbc.aq](../../jdbc/aq/package-summary.md) that return [RAW](../RAW.md)**

    | Modifier and Type  | Method and Description                                                                         |
    |--------------------|------------------------------------------------------------------------------------------------|
    | [`RAW`](../RAW.md) | AQMessage.[`getRAWPayload`](../../jdbc/aq/AQMessage.md)`()`<br>Retrieves the payload as a RAW. |
    | [`RAW`](../RAW.md) | AQMessage.[`getRAWPayload`](../../jdbc/aq/AQMessage.md)`()`<br>Retrieves the payload as a RAW. |

    **Methods in [oracle.jdbc.aq](../../jdbc/aq/package-summary.md) with parameters of type [RAW](../RAW.md)**

    | Modifier and Type | Method and Description                                                                                      |
    |-------------------|-------------------------------------------------------------------------------------------------------------|
    | `void`            | AQMessage.[`setPayload`](../../jdbc/aq/AQMessage.md)`(`[`RAW`](../RAW.md)` payload)`<br>Sets a RAW payload. |
    | `void`            | AQMessage.[`setPayload`](../../jdbc/aq/AQMessage.md)`(`[`RAW`](../RAW.md)` payload)`<br>Sets a RAW payload. |

  - ### Uses of [RAW](../RAW.md) in [oracle.sql](../package-summary.md)

    **Methods in [oracle.sql](../package-summary.md) that return [RAW](../RAW.md)**

    | Modifier and Type           | Method and Description                                                                                                                                                                                                                                          |
    |-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`RAW`](../RAW.md) | RAW.[`newRAW`](../RAW.md)`(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Creates a new RAW from an Object in the manner of the RAW(Object) constructor beginning in 10i R1.                        |
    | `static `[`RAW`](../RAW.md) | RAW.[`newRAW`](../RAW.md)`(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Creates a new RAW from an Object in the manner of the RAW(Object) constructor beginning in 10i R1.                        |
    | `static `[`RAW`](../RAW.md) | RAW.[`oldRAW`](../RAW.md)`(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Creates a new RAW from an Object in the manner of the RAW(Object) constructor in versions of Oracle JDBC 9.2 and earlier. |
    | `static `[`RAW`](../RAW.md) | RAW.[`oldRAW`](../RAW.md)`(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Creates a new RAW from an Object in the manner of the RAW(Object) constructor in versions of Oracle JDBC 9.2 and earlier. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../RAW.md)
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
