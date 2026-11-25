Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleTranslatingConnection.SqlTranslationVersion.md)
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

## Uses of Class oracle.jdbc.OracleTranslatingConnection.SqlTranslationVersion

- **Packages that use [OracleTranslatingConnection.SqlTranslationVersion](../OracleTranslatingConnection.SqlTranslationVersion.md)**

  | Package               | Description                                                                                       |
  |-----------------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc           | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |
  | oracle.jdbc.babelfish | Provides the classes necessary for the support for application migration feature.                 |

- - ### Uses of [OracleTranslatingConnection.SqlTranslationVersion](../OracleTranslatingConnection.SqlTranslationVersion.md) in [oracle.jdbc](../package-summary.md)

    **Methods in [oracle.jdbc](../package-summary.md) that return [OracleTranslatingConnection.SqlTranslationVersion](../OracleTranslatingConnection.SqlTranslationVersion.md)**

    | Modifier and Type                                                                                                           | Method and Description                                                                                                                                                                                                                                                                              |
    |-----------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`OracleTranslatingConnection.SqlTranslationVersion`](../OracleTranslatingConnection.SqlTranslationVersion.md)     | OracleTranslatingConnection.SqlTranslationVersion.[`valueOf`](../OracleTranslatingConnection.SqlTranslationVersion.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Returns the enum constant of this type with the specified name. |
    | `static `[`OracleTranslatingConnection.SqlTranslationVersion`](../OracleTranslatingConnection.SqlTranslationVersion.md)     | OracleTranslatingConnection.SqlTranslationVersion.[`valueOf`](../OracleTranslatingConnection.SqlTranslationVersion.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Returns the enum constant of this type with the specified name. |
    | `static `[`OracleTranslatingConnection.SqlTranslationVersion`](../OracleTranslatingConnection.SqlTranslationVersion.md)`[]` | OracleTranslatingConnection.SqlTranslationVersion.[`values`](../OracleTranslatingConnection.SqlTranslationVersion.md)`()`<br>Returns an array containing the constants of this enum type, in the order they are declared.                                                                           |
    | `static `[`OracleTranslatingConnection.SqlTranslationVersion`](../OracleTranslatingConnection.SqlTranslationVersion.md)`[]` | OracleTranslatingConnection.SqlTranslationVersion.[`values`](../OracleTranslatingConnection.SqlTranslationVersion.md)`()`<br>Returns an array containing the constants of this enum type, in the order they are declared.                                                                           |

    **Methods in [oracle.jdbc](../package-summary.md) that return types with arguments of type [OracleTranslatingConnection.SqlTranslationVersion](../OracleTranslatingConnection.SqlTranslationVersion.md)**

    | Modifier and Type                                                                                                                                                                                                                                                                                               | Method and Description                                                                                                                                                                                                                                                                                                  |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)`<`[`OracleTranslatingConnection.SqlTranslationVersion`](../OracleTranslatingConnection.SqlTranslationVersion.md)`,`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`>` | OracleTranslatingConnection.[`getSqlTranslationVersions`](../OracleTranslatingConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, boolean suppressExceptions)`<br>Returns a map of all the translation versions of the query during SQL Translation. |
    | [`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)`<`[`OracleTranslatingConnection.SqlTranslationVersion`](../OracleTranslatingConnection.SqlTranslationVersion.md)`,`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`>` | OracleTranslatingConnection.[`getSqlTranslationVersions`](../OracleTranslatingConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, boolean suppressExceptions)`<br>Returns a map of all the translation versions of the query during SQL Translation. |

  - ### Uses of [OracleTranslatingConnection.SqlTranslationVersion](../OracleTranslatingConnection.SqlTranslationVersion.md) in [oracle.jdbc.babelfish](../babelfish/package-summary.md)

    **Methods in [oracle.jdbc.babelfish](../babelfish/package-summary.md) that return types with arguments of type [OracleTranslatingConnection.SqlTranslationVersion](../OracleTranslatingConnection.SqlTranslationVersion.md)**

    | Modifier and Type                                                                                                                                                                                                                                                                                               | Method and Description                                                                                                                                                                                                                                                                                            |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)`<`[`OracleTranslatingConnection.SqlTranslationVersion`](../OracleTranslatingConnection.SqlTranslationVersion.md)`,`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`>` | BabelfishConnection.[`getSqlTranslationVersions`](../babelfish/BabelfishConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, boolean suppressExceptions)`<br>Returns a map of all the translation versions of the query during SQL Translation. |
    | [`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)`<`[`OracleTranslatingConnection.SqlTranslationVersion`](../OracleTranslatingConnection.SqlTranslationVersion.md)`,`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`>` | BabelfishConnection.[`getSqlTranslationVersions`](../babelfish/BabelfishConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql, boolean suppressExceptions)`<br>Returns a map of all the translation versions of the query during SQL Translation. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleTranslatingConnection.SqlTranslationVersion.md)
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
