Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleDataFactory.md)
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

## Uses of Interface oracle.jdbc.OracleDataFactory

- **Packages that use [OracleDataFactory](../OracleDataFactory.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |
  | oracle.sql  | A package of classes that represent java SQL types and Oracle specific SQL types.                 |

- - ### Uses of [OracleDataFactory](../OracleDataFactory.md) in [oracle.jdbc](../package-summary.md)

    **Methods in [oracle.jdbc](../package-summary.md) with parameters of type [OracleDataFactory](../OracleDataFactory.md)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                                                                                                                                                                                        |
    |-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | OracleCallableStatement.[`getObject`](../OracleCallableStatement.md)`(int parameterIndex, `[`OracleDataFactory`](../OracleDataFactory.md)` factory)`<br>Returns an instance of `OracleData`, which is returned by the factory's "create" method                                                                               |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | OracleResultSet.[`getObject`](../OracleResultSet.md)`(int columnIndex, `[`OracleDataFactory`](../OracleDataFactory.md)` oracleDataFactory)`<br>Oracle extension Get the column value as an instance of a subclass of OracleData.                                                                                              |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | OracleResultSet.[`getObject`](../OracleResultSet.md)`(int columnIndex, `[`OracleDataFactory`](../OracleDataFactory.md)` oracleDataFactory)`<br>Oracle extension Get the column value as an instance of a subclass of OracleData.                                                                                              |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | OracleCallableStatement.[`getObject`](../OracleCallableStatement.md)`(int parameterIndex, `[`OracleDataFactory`](../OracleDataFactory.md)` factory)`<br>Returns an instance of `OracleData`, which is returned by the factory's "create" method                                                                               |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | OracleResultSet.[`getObject`](../OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`OracleDataFactory`](../OracleDataFactory.md)` oracleDataFactory)`<br>Oracle extension Get the column value as an instance of a subclass of OracleData. |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | OracleResultSet.[`getObject`](../OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`OracleDataFactory`](../OracleDataFactory.md)` oracleDataFactory)`<br>Oracle extension Get the column value as an instance of a subclass of OracleData. |

  - ### Uses of [OracleDataFactory](../OracleDataFactory.md) in [oracle.sql](../../sql/package-summary.md)

    **Methods in [oracle.sql](../../sql/package-summary.md) that return [OracleDataFactory](../OracleDataFactory.md)**

    | Modifier and Type                              | Method and Description                                                                                                                                                                                                                                                                                |
    |------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleDataFactory`](../OracleDataFactory.md) | STRUCT.[`getOracleDataFactory`](../../sql/STRUCT.md)`(`[`Hashtable`](http://download.oracle.com/javase/8/docs/api/java/util/Hashtable.html?is-external=true)` map, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` classname)`<br>Deprecated. <br>  |
    | [`OracleDataFactory`](../OracleDataFactory.md) | STRUCT.[`getOracleDataFactory`](../../sql/STRUCT.md)`(`[`Hashtable`](http://download.oracle.com/javase/8/docs/api/java/util/Hashtable.html?is-external=true)` map, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` classname)`<br>Deprecated. <br>  |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleDataFactory.md)
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
