Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../DatabaseChangeRegistration.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

## Uses of Interface oracle.jdbc.dcn.DatabaseChangeRegistration

- **Packages that use [DatabaseChangeRegistration](../DatabaseChangeRegistration.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |

- - ### Uses of [DatabaseChangeRegistration](../DatabaseChangeRegistration.md) in [oracle.jdbc](../../package-summary.md)

    **Methods in [oracle.jdbc](../../package-summary.md) that return [DatabaseChangeRegistration](../DatabaseChangeRegistration.md)**

    | Modifier and Type                                                | Method and Description                                                                                                                                                                                                                                 |
    |------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`DatabaseChangeRegistration`](../DatabaseChangeRegistration.md) | OracleConnection.[`getDatabaseChangeRegistration`](../../OracleConnection.md)`(int regid)`<br>Maps an existing registration identified by its ID 'regid' with a new DatabaseChangeRegistration object.                                                 |
    | [`DatabaseChangeRegistration`](../DatabaseChangeRegistration.md) | OracleConnectionWrapper.[`getDatabaseChangeRegistration`](../../OracleConnectionWrapper.md)`(int regid)`                                                                                                                                               |
    | [`DatabaseChangeRegistration`](../DatabaseChangeRegistration.md) | OracleConnectionWrapper.[`getDatabaseChangeRegistration`](../../OracleConnectionWrapper.md)`(int regid)`                                                                                                                                               |
    | [`DatabaseChangeRegistration`](../DatabaseChangeRegistration.md) | OracleConnection.[`getDatabaseChangeRegistration`](../../OracleConnection.md)`(int regid)`<br>Maps an existing registration identified by its ID 'regid' with a new DatabaseChangeRegistration object.                                                 |
    | [`DatabaseChangeRegistration`](../DatabaseChangeRegistration.md) | OracleConnection.[`registerDatabaseChangeNotification`](../../OracleConnection.md)`(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` options)`<br>Creates a new database change registration. |
    | [`DatabaseChangeRegistration`](../DatabaseChangeRegistration.md) | OracleConnectionWrapper.[`registerDatabaseChangeNotification`](../../OracleConnectionWrapper.md)`(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` options)`                                  |
    | [`DatabaseChangeRegistration`](../DatabaseChangeRegistration.md) | OracleConnectionWrapper.[`registerDatabaseChangeNotification`](../../OracleConnectionWrapper.md)`(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` options)`                                  |
    | [`DatabaseChangeRegistration`](../DatabaseChangeRegistration.md) | OracleConnection.[`registerDatabaseChangeNotification`](../../OracleConnection.md)`(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` options)`<br>Creates a new database change registration. |

    **Methods in [oracle.jdbc](../../package-summary.md) with parameters of type [DatabaseChangeRegistration](../DatabaseChangeRegistration.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                 |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OracleStatement.[`setDatabaseChangeRegistration`](../../OracleStatement.md)`(`[`DatabaseChangeRegistration`](../DatabaseChangeRegistration.md)` registration)`<br>Associate a Database Change Registration object with this statement. |
    | `void`            | OracleStatement.[`setDatabaseChangeRegistration`](../../OracleStatement.md)`(`[`DatabaseChangeRegistration`](../DatabaseChangeRegistration.md)` registration)`<br>Associate a Database Change Registration object with this statement. |
    | `void`            | OracleConnection.[`unregisterDatabaseChangeNotification`](../../OracleConnection.md)`(`[`DatabaseChangeRegistration`](../DatabaseChangeRegistration.md)` registration)`<br>Deletes a given database change registration.               |
    | `void`            | OracleConnectionWrapper.[`unregisterDatabaseChangeNotification`](../../OracleConnectionWrapper.md)`(`[`DatabaseChangeRegistration`](../DatabaseChangeRegistration.md)` registration)`                                                  |
    | `void`            | OracleConnectionWrapper.[`unregisterDatabaseChangeNotification`](../../OracleConnectionWrapper.md)`(`[`DatabaseChangeRegistration`](../DatabaseChangeRegistration.md)` registration)`                                                  |
    | `void`            | OracleConnection.[`unregisterDatabaseChangeNotification`](../../OracleConnection.md)`(`[`DatabaseChangeRegistration`](../DatabaseChangeRegistration.md)` registration)`<br>Deletes a given database change registration.               |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../DatabaseChangeRegistration.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
