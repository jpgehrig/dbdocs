Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleSavepoint.md)
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

## Uses of Interface oracle.jdbc.OracleSavepoint

- **Packages that use [OracleSavepoint](../OracleSavepoint.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |

- - ### Uses of [OracleSavepoint](../OracleSavepoint.md) in [oracle.jdbc](../package-summary.md)

    **Methods in [oracle.jdbc](../package-summary.md) that return [OracleSavepoint](../OracleSavepoint.md)**

    | Modifier and Type                          | Method and Description                                                                                                                                                                                                                                                                                           |
    |--------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleSavepoint`](../OracleSavepoint.md) | OracleConnection.[`oracleSetSavepoint`](../OracleConnection.md)`()`<br>Creates an unnamed savepoint in the current transaction and returns the new `OracleSavepoint` object that represents it.                                                                                                                  |
    | [`OracleSavepoint`](../OracleSavepoint.md) | OracleConnectionWrapper.[`oracleSetSavepoint`](../OracleConnectionWrapper.md)`()`                                                                                                                                                                                                                                |
    | [`OracleSavepoint`](../OracleSavepoint.md) | OracleConnectionWrapper.[`oracleSetSavepoint`](../OracleConnectionWrapper.md)`()`                                                                                                                                                                                                                                |
    | [`OracleSavepoint`](../OracleSavepoint.md) | OracleConnection.[`oracleSetSavepoint`](../OracleConnection.md)`()`<br>Creates an unnamed savepoint in the current transaction and returns the new `OracleSavepoint` object that represents it.                                                                                                                  |
    | [`OracleSavepoint`](../OracleSavepoint.md) | OracleConnection.[`oracleSetSavepoint`](../OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Creates a savepoint with the given name in the current transaction and returns the new `OracleSavepoint` object that represents it. |
    | [`OracleSavepoint`](../OracleSavepoint.md) | OracleConnectionWrapper.[`oracleSetSavepoint`](../OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`                                                                                                                          |
    | [`OracleSavepoint`](../OracleSavepoint.md) | OracleConnectionWrapper.[`oracleSetSavepoint`](../OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`                                                                                                                          |
    | [`OracleSavepoint`](../OracleSavepoint.md) | OracleConnection.[`oracleSetSavepoint`](../OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Creates a savepoint with the given name in the current transaction and returns the new `OracleSavepoint` object that represents it. |

    **Methods in [oracle.jdbc](../package-summary.md) with parameters of type [OracleSavepoint](../OracleSavepoint.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                    |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OracleConnection.[`oracleReleaseSavepoint`](../OracleConnection.md)`(`[`OracleSavepoint`](../OracleSavepoint.md)` savepoint)`<br>Removes the given `OracleSavepoint` object from the current transaction. |
    | `void`            | OracleConnectionWrapper.[`oracleReleaseSavepoint`](../OracleConnectionWrapper.md)`(`[`OracleSavepoint`](../OracleSavepoint.md)` savepoint)`                                                               |
    | `void`            | OracleConnectionWrapper.[`oracleReleaseSavepoint`](../OracleConnectionWrapper.md)`(`[`OracleSavepoint`](../OracleSavepoint.md)` savepoint)`                                                               |
    | `void`            | OracleConnection.[`oracleReleaseSavepoint`](../OracleConnection.md)`(`[`OracleSavepoint`](../OracleSavepoint.md)` savepoint)`<br>Removes the given `OracleSavepoint` object from the current transaction. |
    | `void`            | OracleConnection.[`oracleRollback`](../OracleConnection.md)`(`[`OracleSavepoint`](../OracleSavepoint.md)` savepoint)`<br>Undoes all changes made after the given `OracleSavepoint` object was set.        |
    | `void`            | OracleConnectionWrapper.[`oracleRollback`](../OracleConnectionWrapper.md)`(`[`OracleSavepoint`](../OracleSavepoint.md)` savepoint)`                                                                       |
    | `void`            | OracleConnectionWrapper.[`oracleRollback`](../OracleConnectionWrapper.md)`(`[`OracleSavepoint`](../OracleSavepoint.md)` savepoint)`                                                                       |
    | `void`            | OracleConnection.[`oracleRollback`](../OracleConnection.md)`(`[`OracleSavepoint`](../OracleSavepoint.md)` savepoint)`<br>Undoes all changes made after the given `OracleSavepoint` object was set.        |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleSavepoint.md)
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
