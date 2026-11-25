Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../CustomDatum.md)
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

## Uses of Interface oracle.sql.CustomDatum

- **Packages that use [CustomDatum](../CustomDatum.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |
  | oracle.sql  | A package of classes that represent java SQL types and Oracle specific SQL types.                 |

- - ### Uses of [CustomDatum](../CustomDatum.md) in [oracle.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) that return [CustomDatum](../CustomDatum.md)**

    | Modifier and Type                  | Method and Description                                                                                                                                                                                                                                         |
    |------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`CustomDatum`](../CustomDatum.md) | OracleResultSet.[`getCustomDatum`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`CustomDatumFactory`](../CustomDatumFactory.md)` factory)`<br>Deprecated.                                                                                                |
    | [`CustomDatum`](../CustomDatum.md) | OracleResultSet.[`getCustomDatum`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`CustomDatumFactory`](../CustomDatumFactory.md)` factory)`<br>Deprecated.                                                                                                |
    | [`CustomDatum`](../CustomDatum.md) | OracleResultSet.[`getCustomDatum`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`CustomDatumFactory`](../CustomDatumFactory.md)` factory)`<br>Deprecated.   |
    | [`CustomDatum`](../CustomDatum.md) | OracleResultSet.[`getCustomDatum`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`CustomDatumFactory`](../CustomDatumFactory.md)` factory)`<br>Deprecated.   |

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) with parameters of type [CustomDatum](../CustomDatum.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                               |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OraclePreparedStatement.[`setCustomDatum`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`CustomDatum`](../CustomDatum.md)` x)`<br>Deprecated.                                                                                                                                                       |
    | `void`            | OraclePreparedStatement.[`setCustomDatum`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`CustomDatum`](../CustomDatum.md)` x)`<br>Deprecated.                                                                                                                                                       |
    | `void`            | OracleCallableStatement.[`setCustomDatum`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`CustomDatum`](../CustomDatum.md)` x)`<br>Sets the designated parameter to an `oracle.sql.CustomDatum`value.   |
    | `void`            | OracleCallableStatement.[`setCustomDatum`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`CustomDatum`](../CustomDatum.md)` x)`<br>Sets the designated parameter to an `oracle.sql.CustomDatum`value.   |
    | `void`            | OraclePreparedStatement.[`setCustomDatumAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`CustomDatum`](../CustomDatum.md)` value)`<br>Sets the designated parameter to a Java CustomDatum value. |
    | `void`            | OraclePreparedStatement.[`setCustomDatumAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`CustomDatum`](../CustomDatum.md)` value)`<br>Sets the designated parameter to a Java CustomDatum value. |
    | `void`            | OracleResultSet.[`updateCustomDatum`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`CustomDatum`](../CustomDatum.md)` value)`<br>Deprecated.                                                                                                                                                                   |
    | `void`            | OracleResultSet.[`updateCustomDatum`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`CustomDatum`](../CustomDatum.md)` value)`<br>Deprecated.                                                                                                                                                                   |
    | `void`            | OracleResultSet.[`updateCustomDatum`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`CustomDatum`](../CustomDatum.md)` value)`<br>Deprecated.                                                                      |
    | `void`            | OracleResultSet.[`updateCustomDatum`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`CustomDatum`](../CustomDatum.md)` value)`<br>Deprecated.                                                                      |

  - ### Uses of [CustomDatum](../CustomDatum.md) in [oracle.sql](../package-summary.md)

    **Methods in [oracle.sql](../package-summary.md) that return [CustomDatum](../CustomDatum.md)**

    | Modifier and Type                  | Method and Description                                                                                                                              |
    |------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`CustomDatum`](../CustomDatum.md) | CustomDatumFactory.[`create`](../CustomDatumFactory.md)`(`[`Datum`](../Datum.md)` d, int sqlType)`<br>create an Object from SQL Type and return it. |
    | [`CustomDatum`](../CustomDatum.md) | CustomDatumFactory.[`create`](../CustomDatumFactory.md)`(`[`Datum`](../Datum.md)` d, int sqlType)`<br>create an Object from SQL Type and return it. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../CustomDatum.md)
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
