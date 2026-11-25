Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleDatabaseMetaData.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleDatabaseException.md)
- [Next Class](OracleDatabaseMetaData.DataTypeSource.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.jdbc

## Class OracleDatabaseMetaData

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.OracleDatabaseMetaData

<!-- -->

- All Implemented Interfaces:
  [DatabaseMetaData](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true), [AdditionalDatabaseMetaData](AdditionalDatabaseMetaData.md), oracle.jdbc.internal.ACProxyable

  ------------------------------------------------------------------------



      public class OracleDatabaseMetaData
      extends Object
      implements oracle.jdbc.internal.AdditionalDatabaseMetaData

  The oracle.jdbc.OracleDatabaseMetaData class along with oracle.jdbc.driver.OracleDatabaseMetaData implement the JDBC 3.0 DatabaseMetaData interface and in ojdbc6.jar and above, the JDBC4.0 DatabaseMetaData interface. Note that the object returned by a call to java.sql.Connection.getMetaData() for a connection from the Oracle driver will be an instance of oracle.jdbc.driver.OracleDatabaseMetaData. There are several proprietary methods which are defined in this class. Only public long getLobMaxLength() will be retained in future versions. The following are superseeded by standard methods public static int getDriverMajorVersionInfo public static int getDriverMinorVersionInfo public static String getDriverVersionInfo and are deprecated. public String getLobPrecision() is no longer meaningful and is deprecated.

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type         | Class and Description                                                                |
    |---------------------------|--------------------------------------------------------------------------------------|
    | `protected static class ` | [`OracleDatabaseMetaData.DataTypeSource`](OracleDatabaseMetaData.DataTypeSource.md)  |

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type                                                                                                          | Field and Description |
    |----------------------------------------------------------------------------------------------------------------------------|-----------------------|
    | `protected `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                | `acProxy`             |
    | `protected oracle.jdbc.internal.OracleConnection`                                                                          | `connection`          |
    | `protected static `[`Pattern`](http://download.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html?is-external=true) | `sqlEscapePattern`    |
    | `protected static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `sqlEscapeRegex`      |
    | `protected static `[`Pattern`](http://download.oracle.com/javase/8/docs/api/java/util/regex/Pattern.html?is-external=true) | `sqlWildcardPattern`  |
    | `protected static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `sqlWildcardRegex`    |

    - ### Fields inherited from interface java.sql.[DatabaseMetaData](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      [`functionColumnIn`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#functionColumnIn)`, `[`functionColumnInOut`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#functionColumnInOut)`, `[`functionColumnOut`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#functionColumnOut)`, `[`functionColumnResult`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#functionColumnResult)`, `[`functionColumnUnknown`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#functionColumnUnknown)`, `[`functionNoNulls`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#functionNoNulls)`, `[`functionNoTable`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#functionNoTable)`, `[`functionNullable`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#functionNullable)`, `[`functionNullableUnknown`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#functionNullableUnknown)`, `[`functionResultUnknown`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#functionResultUnknown)`, `[`functionReturn`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#functionReturn)`, `[`functionReturnsTable`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#functionReturnsTable)`, `[`importedKeyInitiallyDeferred`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#importedKeyInitiallyDeferred)`, `[`importedKeyInitiallyImmediate`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#importedKeyInitiallyImmediate)`, `[`importedKeyNoAction`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#importedKeyNoAction)`, `[`importedKeyNotDeferrable`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#importedKeyNotDeferrable)`, `[`importedKeySetDefault`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#importedKeySetDefault)`, `[`sqlStateSQL`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#sqlStateSQL)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                        |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OracleDatabaseMetaData``(`[`OracleConnection`](OracleConnection.md)` conn)`<br>Deprecated. <br>-- Please use the factory method java.sql.Connection.getMetaData() |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                            | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |--------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                                                    | `allProceduresAreCallable``()`<br>Can all the procedures returned by getProcedures be called by the current user?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `boolean`                                                                                                    | `allTablesAreSelectable``()`<br>Can all the tables returned by getTable be SELECTed by the current user?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `boolean`                                                                                                    | `autoCommitFailureClosesAllResultSets``()`<br>Oracle does not close ResultSets when autocommit fails.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `boolean`                                                                                                    | `dataDefinitionCausesTransactionCommit``()`<br>Does a data definition statement within a transaction force the transaction to commit?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `boolean`                                                                                                    | `dataDefinitionIgnoredInTransactions``()`<br>Is a data definition statement within a transaction ignored?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)  | `datatypeQuery``(`[`OracleDatabaseMetaData.DataTypeSource`](OracleDatabaseMetaData.DataTypeSource.md)` src)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)  | `datatypeQuery``(`[`OracleDatabaseMetaData.DataTypeSource`](OracleDatabaseMetaData.DataTypeSource.md)` src, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` table)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `boolean`                                                                                                    | `deletesAreDetected``(int type)`<br>Implements JDBC 2.0 DatabaseMetaData.deletesAreDetected.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                                                                                    | `doesMaxRowSizeIncludeBlobs``()`<br>Did getMaxRowSize() include LONGVARCHAR and LONGVARBINARY blobs?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `boolean`                                                                                                    | `generatedKeyAlwaysReturned``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getAccessBanner``()`<br>Returns the access banner on this connection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)              | `getACProxy``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getAttributes``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaPattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeNamePattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` attributeNamePattern)`<br>JDBC 3.0 Retrieves a description of the given attribute of the given type for a user-defined type (UDT) that is available in the given schema and catalog.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getAuditBanner``()`<br>Returns the audit banner on this connection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getBestRowIdentifier``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schema, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` table, int scope, boolean nullable)`<br>Get a description of a table's optimal set of columns that uniquely identifies a row.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getCatalogs``()`<br>Get the catalog names available in this database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getCatalogSeparator``()`<br>What's the separator between catalog and table name?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getCatalogTerm``()`<br>What's the database vendor's preferred term for "catalog"?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getClientInfoProperties``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getColumnPrivileges``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaPattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` tableNamePattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnNamePattern)`<br>Get a description of the access rights for a table's columns.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getColumns``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaPattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` tableNamePattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnNamePattern)`<br>Get a description of table columns available in a catalog.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)       | `getConnection``()`<br>Implements JDBC 2.0 DatabaseMetaData.getConnection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getCrossReference``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` primaryCatalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` primarySchema, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` primaryTable, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` foreignCatalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` foreignSchema, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` foreignTable)`<br>Get a description of the foreign key columns in the foreign key table that reference the primary key columns of the primary key table (describe how one table imports another's key.) This should normally return a single foreign key/primary key pair (most tables only import a foreign key from a table once.) They are ordered by FKTABLE_CAT, FKTABLE_SCHEM, FKTABLE_NAME, and KEY_SEQ. |
    | `int`                                                                                                        | `getDatabaseMajorVersion``()`<br>JDBC 3.0 Retrieves the major version number of the underlying database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `int`                                                                                                        | `getDatabaseMinorVersion``()`<br>JDBC 3.0 Retrieves the minor version number of the underlying database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getDatabaseProductName``()`<br>What's the name of this database product?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getDatabaseProductVersion``()`<br>What's the version of this database product?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `int`                                                                                                        | `getDefaultTransactionIsolation``()`<br>What's the database's default transaction isolation level? The values are defined in java.sql.Connection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `int`                                                                                                        | `getDriverMajorVersion``()`<br>What's this JDBC driver's major version number?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static int`                                                                                                 | `getDriverMajorVersionInfo``()`<br>Deprecated. <br>-- use standard getDriverMajorVersion()                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `int`                                                                                                        | `getDriverMinorVersion``()`<br>What's this JDBC driver's minor version number?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static int`                                                                                                 | `getDriverMinorVersionInfo``()`<br>Deprecated. <br>-- use JDBC standard method getDriverMinorVersion                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getDriverName``()`<br>What's the name of this JDBC driver?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getDriverNameInfo``()`<br>What's the name of this JDBC driver?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getDriverVersion``()`<br>What's the version of this JDBC driver?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getDriverVersionInfo``()`<br>Deprecated. <br>-- use standard getDriverVersion()                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getExportedKeys``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schema, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` table)`<br>Get a description of a foreign key columns that reference a table's primary key columns (the foreign keys exported by a table).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getExtraNameCharacters``()`<br>Get all the "extra" characters that can be used in unquoted identifier names (those beyond a-z, 0-9 and \_).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getFunctionColumns``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaPattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` functionNamePattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnNamePattern)`<br>Retrieves a description of the given catalog's system or user function parameters and return type.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getFunctions``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaPattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` functionNamePattern)`<br>Return a result set that describes the matching functions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `protected int`                                                                                              | `getIdentifierLength``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getIdentifierQuoteString``()`<br>What's the string used to quote SQL identifiers? This returns a space " " if identifier quoting isn't supported.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getImportedKeys``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schema, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` table)`<br>Get a description of the primary key columns that are referenced by a table's foreign key columns (the primary keys imported by a table).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getIndexInfo``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schema, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` table, boolean unique, boolean approximate)`<br>Get a description of a table's indices and statistics.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `int`                                                                                                        | `getJDBCMajorVersion``()`<br>JDBC 3.0 Retrieves the major JDBC version number for this driver.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `int`                                                                                                        | `getJDBCMinorVersion``()`<br>JDBC 3.0 Retrieves the minor JDBC version number for this driver.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `long`                                                                                                       | `getLobMaxLength``()`<br>The max size of a lob on the server for this connection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getLobPrecision``()`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `int`                                                                                                        | `getMaxBinaryLiteralLength``()`<br>How many hex characters can you have in an inline binary literal?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `int`                                                                                                        | `getMaxCatalogNameLength``()`<br>What's the maximum length of a catalog name?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `int`                                                                                                        | `getMaxCharLiteralLength``()`<br>What's the max length for a character literal?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `int`                                                                                                        | `getMaxColumnNameLength``()`<br>What's the limit on column name length?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `int`                                                                                                        | `getMaxColumnsInGroupBy``()`<br>What's the maximum number of columns in a "GROUP BY" clause?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `int`                                                                                                        | `getMaxColumnsInIndex``()`<br>What's the maximum number of columns allowed in an index?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `int`                                                                                                        | `getMaxColumnsInOrderBy``()`<br>What's the maximum number of columns in an "ORDER BY" clause?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `int`                                                                                                        | `getMaxColumnsInSelect``()`<br>What's the maximum number of columns in a "SELECT" list?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `int`                                                                                                        | `getMaxColumnsInTable``()`<br>What's maximum number of columns in a table?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `int`                                                                                                        | `getMaxConnections``()`<br>How many active connections can we have at a time to this database?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `int`                                                                                                        | `getMaxCursorNameLength``()`<br>What's the maximum cursor name length?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `int`                                                                                                        | `getMaxIndexLength``()`<br>What's the maximum length of an index (in bytes)?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `int`                                                                                                        | `getMaxProcedureNameLength``()`<br>What's the maximum length of a procedure name?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `int`                                                                                                        | `getMaxRowSize``()`<br>What's the maximum length of a single row?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `int`                                                                                                        | `getMaxSchemaNameLength``()`<br>What's the maximum length allowed for a schema name?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `int`                                                                                                        | `getMaxStatementLength``()`<br>What's the maximum length of a SQL statement?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `int`                                                                                                        | `getMaxStatements``()`<br>How many active statements can we have open at one time to this database?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `int`                                                                                                        | `getMaxTableNameLength``()`<br>What's the maximum length of a table name?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `int`                                                                                                        | `getMaxTablesInSelect``()`<br>What's the maximum number of tables in a SELECT?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `int`                                                                                                        | `getMaxUserNameLength``()`<br>What's the maximum length of a user name?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getNumericFunctions``()`<br>Get a comma separated list of math functions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | [`OracleTypeMetaData`](OracleTypeMetaData.md)                                                                | `getOracleTypeMetaData``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sqlTypeName)`<br>Return the type metadata for a named type.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getPrimaryKeys``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schema, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` table)`<br>Get a description of a table's primary key columns.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getProcedureColumns``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaPattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` procedureNamePattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnNamePattern)`<br>Get a description of a catalog's stored procedure parameters and result columns.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getProcedures``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaPattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` procedureNamePattern)`<br>Get a description of stored procedures available in a catalog.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getProcedureTerm``()`<br>What's the database vendor's preferred term for "procedure"?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getPseudoColumns``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaPattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` tableNamePattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnNamePattern)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `int`                                                                                                        | `getResultSetHoldability``()`<br>JDBC 3.0 Retrieves the default holdability of this `ResultSet` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`RowIdLifetime`](http://download.oracle.com/javase/8/docs/api/java/sql/RowIdLifetime.html?is-external=true) | `getRowIdLifetime``()`<br>Oracle rowids are valid across all sessions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getSchemas``()`<br>Get the schema names available in this database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getSchemas``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaPattern)`<br>Return the schemas that match the given pattern.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getSchemaTerm``()`<br>What's the database vendor's preferred term for "schema"?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getSearchStringEscape``()`<br>This is the string that can be used to escape '\_' or '%' in the string pattern style catalog search parameters.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getSQLKeywords``()`<br>Get a comma separated list of all a database's SQL keywords that are NOT also SQL92 keywords.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `int`                                                                                                        | `getSQLStateType``()`<br>JDBC 3.0 Indicates whether the SQLSTATEs returned by `SQLException.getSQLState` is X/Open (now known as Open Group) SQL CLI or SQL99.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getStringFunctions``()`<br>Get a comma separated list of string functions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getSuperTables``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaPattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` tableNamePattern)`<br>JDBC 3.0 Retrieves a description of the table hierarchies defined in a particular schema in this database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getSuperTypes``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaPattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeNamePattern)`<br>JDBC 3.0 Retrieves a description of the user-defined type (UDT) hierarchies defined in a particular schema in this database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getSystemFunctions``()`<br>Get a comma separated list of system functions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getTablePrivileges``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaPattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` tableNamePattern)`<br>Get a description of the access rights for each table available in a catalog.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getTables``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaPattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` tableNamePattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] types)`<br>Get a description of tables available in a catalog.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getTableTypes``()`<br>Get the table types available in this database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getTimeDateFunctions``()`<br>Get a comma separated list of time and date functions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getTypeInfo``()`<br>Get a description of all the standard SQL types supported by this database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getUDTs``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaPattern, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeNamePattern, int[] types)`<br>Implements JDBC 2.0 DatabaseMetaData::getUDTs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getURL``()`<br>What's the url for this database?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)              | `getUserName``()`<br>What's our user name as known to the database?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)         | `getVersionColumns``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` catalog, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schema, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` table)`<br>Get a description of a table's columns that are automatically updated when any value in a row is updated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `protected boolean`                                                                                          | `hasSqlWildcard``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `boolean`                                                                                                    | `insertsAreDetected``(int type)`<br>Implements JDBC 2.0 DatabaseMetaData.insertsAreDetected.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                                                                                    | `isCatalogAtStart``()`<br>Does a catalog appear at the start of a qualified table name? (Otherwise it appears at the end)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                                                                                    | `isCompatible122OrGreater``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `boolean`                                                                                                    | `isReadOnly``()`<br>Is the database in read-only mode?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `boolean`                                                                                                    | `isServerBigSCN``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `boolean`                                                                                                    | `isWrapperFor``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)`<?> iface)`<br>Since this class is not a wrapper, just check to see if this implements the requested interface.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `boolean`                                                                                                    | `locatorsUpdateCopy``()`<br>JDBC 3.0                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `boolean`                                                                                                    | `nullPlusNonNullIsNull``()`<br>Are concatenations between NULL and non-NULL values NULL? A JDBC compliant driver always returns true.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `boolean`                                                                                                    | `nullsAreSortedAtEnd``()`<br>Are NULL values sorted at the end regardless of sort order?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `boolean`                                                                                                    | `nullsAreSortedAtStart``()`<br>Are NULL values sorted at the start regardless of sort order?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                                                                                    | `nullsAreSortedHigh``()`<br>Are NULL values sorted high?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `boolean`                                                                                                    | `nullsAreSortedLow``()`<br>Are NULL values sorted low?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `boolean`                                                                                                    | `othersDeletesAreVisible``(int type)`<br>Implements JDBC 2.0 DatabaseMetaData..                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `boolean`                                                                                                    | `othersInsertsAreVisible``(int type)`<br>Implements JDBC 2.0 DatabaseMetaData.othersInsertsAreVisible.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `boolean`                                                                                                    | `othersUpdatesAreVisible``(int type)`<br>Implements JDBC 2.0 DatabaseMetaData..                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `boolean`                                                                                                    | `ownDeletesAreVisible``(int type)`<br>Implements JDBC 2.0 DatabaseMetaData.ownDeletesAreVisible.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `boolean`                                                                                                    | `ownInsertsAreVisible``(int type)`<br>Implements JDBC 2.0 DatabaseMetaData.ownInsertsAreVisible.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `boolean`                                                                                                    | `ownUpdatesAreVisible``(int type)`<br>Implements JDBC 2.0 DatabaseMetaData.ownUpdatesAreVisible.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `void`                                                                                                       | `setACProxy``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` w)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `boolean`                                                                                                    | `storesLowerCaseIdentifiers``()`<br>Does the database treat mixed case unquoted SQL identifiers as case insensitive and store them in lower case?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `boolean`                                                                                                    | `storesLowerCaseQuotedIdentifiers``()`<br>Does the database treat mixed case quoted SQL identifiers as case insensitive and store them in lower case?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `boolean`                                                                                                    | `storesMixedCaseIdentifiers``()`<br>Does the database treat mixed case unquoted SQL identifiers as case insensitive and store them in mixed case?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `boolean`                                                                                                    | `storesMixedCaseQuotedIdentifiers``()`<br>Does the database treat mixed case quoted SQL identifiers as case insensitive and store them in mixed case?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `boolean`                                                                                                    | `storesUpperCaseIdentifiers``()`<br>Does the database treat mixed case unquoted SQL identifiers as case insensitive and store them in upper case?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `boolean`                                                                                                    | `storesUpperCaseQuotedIdentifiers``()`<br>Does the database treat mixed case quoted SQL identifiers as case insensitive and store them in upper case?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `protected `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)  | `stripSqlEscapes``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` s)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `boolean`                                                                                                    | `supportsAlterTableWithAddColumn``()`<br>Is "ALTER TABLE" with add column supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `boolean`                                                                                                    | `supportsAlterTableWithDropColumn``()`<br>Is "ALTER TABLE" with drop column supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `boolean`                                                                                                    | `supportsANSI92EntryLevelSQL``()`<br>Is the ANSI92 entry level SQL grammar supported? All JDBC compliant drivers must return true.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `boolean`                                                                                                    | `supportsANSI92FullSQL``()`<br>Is the ANSI92 full SQL grammar supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `boolean`                                                                                                    | `supportsANSI92IntermediateSQL``()`<br>Is the ANSI92 intermediate SQL grammar supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `boolean`                                                                                                    | `supportsBatchUpdates``()`<br>Implements JDBC 2.0 DatabaseMetaData::supportBatchUpdates.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `boolean`                                                                                                    | `supportsCatalogsInDataManipulation``()`<br>Can a catalog name be used in a data manipulation statement?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `boolean`                                                                                                    | `supportsCatalogsInIndexDefinitions``()`<br>Can a catalog name be used in a index definition statement?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `boolean`                                                                                                    | `supportsCatalogsInPrivilegeDefinitions``()`<br>Can a catalog name be used in a privilege definition statement?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `boolean`                                                                                                    | `supportsCatalogsInProcedureCalls``()`<br>Can a catalog name be used in a procedure call statement?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `boolean`                                                                                                    | `supportsCatalogsInTableDefinitions``()`<br>Can a catalog name be used in a table definition statement?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `boolean`                                                                                                    | `supportsColumnAliasing``()`<br>Is column aliasing supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `boolean`                                                                                                    | `supportsConvert``()`<br>Is the CONVERT function between SQL types supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `boolean`                                                                                                    | `supportsConvert``(int fromType, int toType)`<br>Is CONVERT between the given SQL types supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `boolean`                                                                                                    | `supportsCoreSQLGrammar``()`<br>Is the ODBC Core SQL grammar supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `boolean`                                                                                                    | `supportsCorrelatedSubqueries``()`<br>Are correlated subqueries supported? A JDBC compliant driver always returns true.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `boolean`                                                                                                    | `supportsDataDefinitionAndDataManipulationTransactions``()`<br>Are both data definition and data manipulation statements within a transaction supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `boolean`                                                                                                    | `supportsDataManipulationTransactionsOnly``()`<br>Are only data manipulation statements within a transaction supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `boolean`                                                                                                    | `supportsDifferentTableCorrelationNames``()`<br>If table correlation names are supported, are they restricted to be different from the names of the tables?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `boolean`                                                                                                    | `supportsExpressionsInOrderBy``()`<br>Are expressions in "ORDER BY" lists supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `boolean`                                                                                                    | `supportsExtendedSQLGrammar``()`<br>Is the ODBC Extended SQL grammar supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `boolean`                                                                                                    | `supportsFullOuterJoins``()`<br>Are full nested outer joins supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `boolean`                                                                                                    | `supportsGetGeneratedKeys``()`<br>JDBC 3.0 Retrieves whether auto-generated keys can be retrieved after a statement has been executed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `boolean`                                                                                                    | `supportsGroupBy``()`<br>Is some form of "GROUP BY" clause supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `boolean`                                                                                                    | `supportsGroupByBeyondSelect``()`<br>Can a "GROUP BY" clause add columns not in the SELECT provided it specifies all the columns in the SELECT?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `boolean`                                                                                                    | `supportsGroupByUnrelated``()`<br>Can a "GROUP BY" clause use columns not in the SELECT?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `boolean`                                                                                                    | `supportsIntegrityEnhancementFacility``()`<br>Is the SQL Integrity Enhancement Facility supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `boolean`                                                                                                    | `supportsLikeEscapeClause``()`<br>Is the escape character in "LIKE" clauses supported? A JDBC compliant driver always returns true.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `boolean`                                                                                                    | `supportsLimitedOuterJoins``()`<br>Is there limited support for outer joins? (This will be true if supportFullOuterJoins is true.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `boolean`                                                                                                    | `supportsMinimumSQLGrammar``()`<br>Is the ODBC Minimum SQL grammar supported? All JDBC compliant drivers must return true.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `boolean`                                                                                                    | `supportsMixedCaseIdentifiers``()`<br>Does the database treat mixed case unquoted SQL identifiers as case sensitive and as a result store them in mixed case? A JDBC compliant driver will always return false.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `boolean`                                                                                                    | `supportsMixedCaseQuotedIdentifiers``()`<br>Does the database treat mixed case quoted SQL identifiers as case sensitive and as a result store them in mixed case? A JDBC compliant driver will always return false.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `boolean`                                                                                                    | `supportsMultipleOpenResults``()`<br>JDBC 3.0 Retrieves whether it is possible to have multiple `ResultSet` objects returned from a `CallableStatement` object simultaneously.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `boolean`                                                                                                    | `supportsMultipleResultSets``()`<br>Are multiple ResultSets from a single execute supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                                                                                    | `supportsMultipleTransactions``()`<br>Can we have multiple transactions open at once (on different connections)?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `boolean`                                                                                                    | `supportsNamedParameters``()`<br>JDBC 3.0 Retrieves whether this database supports named parameters to callable statements.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `boolean`                                                                                                    | `supportsNonNullableColumns``()`<br>Can columns be defined as non-nullable? A JDBC compliant driver always returns true.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `boolean`                                                                                                    | `supportsOpenCursorsAcrossCommit``()`<br>Can cursors remain open across commits?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `boolean`                                                                                                    | `supportsOpenCursorsAcrossRollback``()`<br>Can cursors remain open across rollbacks?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `boolean`                                                                                                    | `supportsOpenStatementsAcrossCommit``()`<br>Can statements remain open across commits?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `boolean`                                                                                                    | `supportsOpenStatementsAcrossRollback``()`<br>Can statements remain open across rollbacks?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `boolean`                                                                                                    | `supportsOrderByUnrelated``()`<br>Can an "ORDER BY" clause use columns not in the SELECT?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                                                                                    | `supportsOuterJoins``()`<br>Is some form of outer join supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `boolean`                                                                                                    | `supportsPositionedDelete``()`<br>Is positioned DELETE supported? NOTE: Though Oracle supports positional delete through the use of ROWID positional delete as specified by SQLJ92 standard is not supported which is being followed by JDBC 2.1 API Spec.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `boolean`                                                                                                    | `supportsPositionedUpdate``()`<br>Is positioned UPDATE supported? NOTE: Though Oracle supports positional updates through the use of ROWID positional updates as specified by SQLJ92 standard is not supported which is being followed by JDBC 2.1 API Spec.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                                                                                    | `supportsResultSetConcurrency``(int type, int concurrency)`<br>Implements JDBC 2.0 DatabaseMetaData.supportsResultSetConcurrency.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `boolean`                                                                                                    | `supportsResultSetHoldability``(int holdability)`<br>JDBC 3.0 Retrieves whether this database supports the given result set holdability.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `boolean`                                                                                                    | `supportsResultSetType``(int type)`<br>Implements JDBC 2.0 DatabaseMetaData.supportsResultSetType.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `boolean`                                                                                                    | `supportsSavepoints``()`<br>JDBC 3.0 Retrieves whether this database supports savepoints.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                                                                                    | `supportsSchemasInDataManipulation``()`<br>Can a schema name be used in a data manipulation statement?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `boolean`                                                                                                    | `supportsSchemasInIndexDefinitions``()`<br>Can a schema name be used in an index definition statement?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `boolean`                                                                                                    | `supportsSchemasInPrivilegeDefinitions``()`<br>Can a schema name be used in a privilege definition statement?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `boolean`                                                                                                    | `supportsSchemasInProcedureCalls``()`<br>Can a schema name be used in a procedure call statement?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `boolean`                                                                                                    | `supportsSchemasInTableDefinitions``()`<br>Can a schema name be used in a table definition statement?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `boolean`                                                                                                    | `supportsSelectForUpdate``()`<br>Is SELECT for UPDATE supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `boolean`                                                                                                    | `supportsStatementPooling``()`<br>JDBC 3.0                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `boolean`                                                                                                    | `supportsStoredFunctionsUsingCallSyntax``()`<br>Oracle supports using the JDBC escape syntax to call PLSQL functions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `boolean`                                                                                                    | `supportsStoredProcedures``()`<br>Are stored procedure calls using the stored procedure escape syntax supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `boolean`                                                                                                    | `supportsSubqueriesInComparisons``()`<br>Are subqueries in comparison expressions supported? A JDBC compliant driver always returns true.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                                                                                    | `supportsSubqueriesInExists``()`<br>Are subqueries in exists expressions supported? A JDBC compliant driver always returns true.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `boolean`                                                                                                    | `supportsSubqueriesInIns``()`<br>Are subqueries in "in" statements supported? A JDBC compliant driver always returns true.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `boolean`                                                                                                    | `supportsSubqueriesInQuantifieds``()`<br>Are subqueries in quantified expressions supported? A JDBC compliant driver always returns true.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                                                                                    | `supportsTableCorrelationNames``()`<br>Are table correlation names supported? A JDBC compliant driver always returns true.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `boolean`                                                                                                    | `supportsTransactionIsolationLevel``(int level)`<br>Does the database support the given transaction isolation level?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `boolean`                                                                                                    | `supportsTransactions``()`<br>Are transactions supported? If not, commit is a noop and the isolation level is TRANSACTION_NONE.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `boolean`                                                                                                    | `supportsUnion``()`<br>Is SQL UNION supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `boolean`                                                                                                    | `supportsUnionAll``()`<br>Is SQL UNION ALL supported?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `<T> T`                                                                                                      | `unwrap``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)`<T> iface)`<br>Since this class is not a wrapper, just check to see if this implements the requested interface.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `boolean`                                                                                                    | `updatesAreDetected``(int type)`<br>Implements JDBC 2.0 DatabaseMetaData.updatesAreDetected.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                                                                                    | `usesLocalFilePerTable``()`<br>Does the database use a file for each table?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `boolean`                                                                                                    | `usesLocalFiles``()`<br>Does the database store tables in a local file?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface java.sql.[DatabaseMetaData](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      [`getMaxLogicalLobSize`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxLogicalLobSize__)`, `[`supportsRefCursors`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsRefCursors__)

<!-- -->

- - ### Field Detail

    - #### connection

          protected oracle.jdbc.internal.OracleConnection connection

    <!-- -->

    - #### sqlWildcardRegex

          protected static final String sqlWildcardRegex

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### sqlWildcardPattern

          protected static Pattern sqlWildcardPattern

    <!-- -->

    - #### sqlEscapeRegex

          protected static final String sqlEscapeRegex

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### sqlEscapePattern

          protected static Pattern sqlEscapePattern

    <!-- -->

    - #### acProxy

          protected Object acProxy

  <!-- -->

  - ### Constructor Detail

    - #### OracleDatabaseMetaData

          public OracleDatabaseMetaData(OracleConnection conn)

      Deprecated. -- Please use the factory method java.sql.Connection.getMetaData()

  <!-- -->

  - ### Method Detail

    - #### allProceduresAreCallable

          public boolean allProceduresAreCallable()
                                           throws SQLException

      Can all the procedures returned by getProcedures be called by the current user?
      Specified by:
      [`allProceduresAreCallable`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#allProceduresAreCallable__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### allTablesAreSelectable

          public boolean allTablesAreSelectable()
                                         throws SQLException

      Can all the tables returned by getTable be SELECTed by the current user?
      Specified by:
      [`allTablesAreSelectable`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#allTablesAreSelectable__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getURL

          public String getURL()
                        throws SQLException

      What's the url for this database?
      Specified by:
      [`getURL`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getURL__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the url or null if it can't be generated

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getUserName

          public String getUserName()
                             throws SQLException

      What's our user name as known to the database?
      Specified by:
      [`getUserName`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getUserName__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      our database user name

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isReadOnly

          public boolean isReadOnly()
                             throws SQLException

      Is the database in read-only mode?
      Specified by:
      [`isReadOnly`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#isReadOnly__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### nullsAreSortedHigh

          public boolean nullsAreSortedHigh()
                                     throws SQLException

      Are NULL values sorted high?
      Specified by:
      [`nullsAreSortedHigh`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#nullsAreSortedHigh__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### nullsAreSortedLow

          public boolean nullsAreSortedLow()
                                    throws SQLException

      Are NULL values sorted low?
      Specified by:
      [`nullsAreSortedLow`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#nullsAreSortedLow__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### nullsAreSortedAtStart

          public boolean nullsAreSortedAtStart()
                                        throws SQLException

      Are NULL values sorted at the start regardless of sort order?
      Specified by:
      [`nullsAreSortedAtStart`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#nullsAreSortedAtStart__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### nullsAreSortedAtEnd

          public boolean nullsAreSortedAtEnd()
                                      throws SQLException

      Are NULL values sorted at the end regardless of sort order?
      Specified by:
      [`nullsAreSortedAtEnd`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#nullsAreSortedAtEnd__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDatabaseProductName

          public String getDatabaseProductName()
                                        throws SQLException

      What's the name of this database product?
      Specified by:
      [`getDatabaseProductName`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getDatabaseProductName__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      database product name

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDatabaseProductVersion

          public String getDatabaseProductVersion()
                                           throws SQLException

      What's the version of this database product?
      Specified by:
      [`getDatabaseProductVersion`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getDatabaseProductVersion__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      database version

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDriverName

          public String getDriverName()
                               throws SQLException

      What's the name of this JDBC driver?
      Specified by:
      [`getDriverName`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getDriverName__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      JDBC driver name

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDriverVersion

          public String getDriverVersion()
                                  throws SQLException

      What's the version of this JDBC driver?
      Specified by:
      [`getDriverVersion`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getDriverVersion__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      JDBC driver version

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDriverMajorVersion

          public int getDriverMajorVersion()

      What's this JDBC driver's major version number?
      Specified by:
      [`getDriverMajorVersion`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getDriverMajorVersion__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      JDBC driver major version

    <!-- -->

    - #### getDriverMinorVersion

          public int getDriverMinorVersion()

      What's this JDBC driver's minor version number?
      Specified by:
      [`getDriverMinorVersion`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getDriverMinorVersion__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      JDBC driver minor version number

    <!-- -->

    - #### usesLocalFiles

          public boolean usesLocalFiles()
                                 throws SQLException

      Does the database store tables in a local file?
      Specified by:
      [`usesLocalFiles`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#usesLocalFiles__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### usesLocalFilePerTable

          public boolean usesLocalFilePerTable()
                                        throws SQLException

      Does the database use a file for each table?
      Specified by:
      [`usesLocalFilePerTable`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#usesLocalFilePerTable__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if the database uses a local file for each table

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsMixedCaseIdentifiers

          public boolean supportsMixedCaseIdentifiers()
                                               throws SQLException

      Does the database treat mixed case unquoted SQL identifiers as case sensitive and as a result store them in mixed case? A JDBC compliant driver will always return false.
      Specified by:
      [`supportsMixedCaseIdentifiers`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsMixedCaseIdentifiers__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### storesUpperCaseIdentifiers

          public boolean storesUpperCaseIdentifiers()
                                             throws SQLException

      Does the database treat mixed case unquoted SQL identifiers as case insensitive and store them in upper case?
      Specified by:
      [`storesUpperCaseIdentifiers`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#storesUpperCaseIdentifiers__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### storesLowerCaseIdentifiers

          public boolean storesLowerCaseIdentifiers()
                                             throws SQLException

      Does the database treat mixed case unquoted SQL identifiers as case insensitive and store them in lower case?
      Specified by:
      [`storesLowerCaseIdentifiers`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#storesLowerCaseIdentifiers__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### storesMixedCaseIdentifiers

          public boolean storesMixedCaseIdentifiers()
                                             throws SQLException

      Does the database treat mixed case unquoted SQL identifiers as case insensitive and store them in mixed case?
      Specified by:
      [`storesMixedCaseIdentifiers`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#storesMixedCaseIdentifiers__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsMixedCaseQuotedIdentifiers

          public boolean supportsMixedCaseQuotedIdentifiers()
                                                     throws SQLException

      Does the database treat mixed case quoted SQL identifiers as case sensitive and as a result store them in mixed case? A JDBC compliant driver will always return false.
      Specified by:
      [`supportsMixedCaseQuotedIdentifiers`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsMixedCaseQuotedIdentifiers__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### storesUpperCaseQuotedIdentifiers

          public boolean storesUpperCaseQuotedIdentifiers()
                                                   throws SQLException

      Does the database treat mixed case quoted SQL identifiers as case insensitive and store them in upper case?
      Specified by:
      [`storesUpperCaseQuotedIdentifiers`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#storesUpperCaseQuotedIdentifiers__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### storesLowerCaseQuotedIdentifiers

          public boolean storesLowerCaseQuotedIdentifiers()
                                                   throws SQLException

      Does the database treat mixed case quoted SQL identifiers as case insensitive and store them in lower case?
      Specified by:
      [`storesLowerCaseQuotedIdentifiers`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#storesLowerCaseQuotedIdentifiers__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### storesMixedCaseQuotedIdentifiers

          public boolean storesMixedCaseQuotedIdentifiers()
                                                   throws SQLException

      Does the database treat mixed case quoted SQL identifiers as case insensitive and store them in mixed case?
      Specified by:
      [`storesMixedCaseQuotedIdentifiers`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#storesMixedCaseQuotedIdentifiers__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getIdentifierQuoteString

          public String getIdentifierQuoteString()
                                          throws SQLException

      What's the string used to quote SQL identifiers? This returns a space " " if identifier quoting isn't supported. A JDBC compliant driver always uses a double quote character.
      Specified by:
      [`getIdentifierQuoteString`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getIdentifierQuoteString__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the quoting string

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSQLKeywords

          public String getSQLKeywords()
                                throws SQLException

      Get a comma separated list of all a database's SQL keywords that are NOT also SQL92 keywords.
      Specified by:
      [`getSQLKeywords`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getSQLKeywords__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the list

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getNumericFunctions

          public String getNumericFunctions()
                                     throws SQLException

      Get a comma separated list of math functions. The following are supported
      - ABS
      - ACOS
      - ASIN
      - ATAN
      - ATAN2
      - CEILING
      - COS
      - EXP
      - FLOOR
      - LOG
      - LOG10
      - MOD
      - PI
      - POWER
      - ROUND
      - SIGN
      - SIN
      - SQRT
      - TAN
      - TRUNCATE

      Specified by:
      [`getNumericFunctions`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getNumericFunctions__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the list

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getStringFunctions

          public String getStringFunctions()
                                    throws SQLException

      Get a comma separated list of string functions. The following are supported
      - ASCII
      - CHAR
      - CONCAT
      - LCASE
      - LENGTH
      - LTRIM
      - REPLACE
      - RTRIM
      - SOUNDEX
      - SUBSTRING
      - UCASE

      In addition, the following are supported in a JDBC 4.0 environment
      - OCTET_LENGTH
      - CHAR_LENGTH
      - CHARACTER_LENGTH

      Specified by:
      [`getStringFunctions`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getStringFunctions__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the list

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSystemFunctions

          public String getSystemFunctions()
                                    throws SQLException

      Get a comma separated list of system functions. The following are supported
      - USER

      Specified by:
      [`getSystemFunctions`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getSystemFunctions__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the list

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getTimeDateFunctions

          public String getTimeDateFunctions()
                                      throws SQLException

      Get a comma separated list of time and date functions. The following are supported
      - CURDATE
      - HOUR
      - MINUTE
      - MONTH
      - SECOND
      - YEAR

      In addition, the following are supported in a JDBC 4.0 environment.
      - CURRENT_DATE
      - CURRENT_TIMESTAMP
      - EXTRACT

      Specified by:
      [`getTimeDateFunctions`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getTimeDateFunctions__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the list

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSearchStringEscape

          public String getSearchStringEscape()
                                       throws SQLException

      This is the string that can be used to escape '\_' or '%' in the string pattern style catalog search parameters.
      The '\_' character represents any single character.

      The '%' character represents any sequence of zero or more characters.

      Specified by:
      [`getSearchStringEscape`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getSearchStringEscape__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the string used to escape wildcard characters

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getExtraNameCharacters

          public String getExtraNameCharacters()
                                        throws SQLException

      Get all the "extra" characters that can be used in unquoted identifier names (those beyond a-z, 0-9 and \_).
      Specified by:
      [`getExtraNameCharacters`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getExtraNameCharacters__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the string containing the extra characters

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsAlterTableWithAddColumn

          public boolean supportsAlterTableWithAddColumn()
                                                  throws SQLException

      Is "ALTER TABLE" with add column supported?
      Specified by:
      [`supportsAlterTableWithAddColumn`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsAlterTableWithAddColumn__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsAlterTableWithDropColumn

          public boolean supportsAlterTableWithDropColumn()
                                                   throws SQLException

      Is "ALTER TABLE" with drop column supported?
      Specified by:
      [`supportsAlterTableWithDropColumn`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsAlterTableWithDropColumn__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsColumnAliasing

          public boolean supportsColumnAliasing()
                                         throws SQLException

      Is column aliasing supported?
      If so, the SQL AS clause can be used to provide names for computed columns or to provide alias names for columns as required. A JDBC compliant driver always returns true.

      Specified by:
      [`supportsColumnAliasing`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsColumnAliasing__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### nullPlusNonNullIsNull

          public boolean nullPlusNonNullIsNull()
                                        throws SQLException

      Are concatenations between NULL and non-NULL values NULL? A JDBC compliant driver always returns true.
      Specified by:
      [`nullPlusNonNullIsNull`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#nullPlusNonNullIsNull__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsConvert

          public boolean supportsConvert()
                                  throws SQLException

      Is the CONVERT function between SQL types supported?
      Specified by:
      [`supportsConvert`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsConvert__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsConvert

          public boolean supportsConvert(int fromType,
                                         int toType)
                                  throws SQLException

      Is CONVERT between the given SQL types supported?
      Specified by:
      [`supportsConvert`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsConvert_int_int_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `fromType` - the type to convert from

      `toType` - the type to convert to

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Types`](http://download.oracle.com/javase/8/docs/api/java/sql/Types.html?is-external=true)

    <!-- -->

    - #### supportsTableCorrelationNames

          public boolean supportsTableCorrelationNames()
                                                throws SQLException

      Are table correlation names supported? A JDBC compliant driver always returns true.
      Specified by:
      [`supportsTableCorrelationNames`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsTableCorrelationNames__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsDifferentTableCorrelationNames

          public boolean supportsDifferentTableCorrelationNames()
                                                         throws SQLException

      If table correlation names are supported, are they restricted to be different from the names of the tables?
      Specified by:
      [`supportsDifferentTableCorrelationNames`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsDifferentTableCorrelationNames__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsExpressionsInOrderBy

          public boolean supportsExpressionsInOrderBy()
                                               throws SQLException

      Are expressions in "ORDER BY" lists supported?
      Specified by:
      [`supportsExpressionsInOrderBy`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsExpressionsInOrderBy__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsOrderByUnrelated

          public boolean supportsOrderByUnrelated()
                                           throws SQLException

      Can an "ORDER BY" clause use columns not in the SELECT?
      Specified by:
      [`supportsOrderByUnrelated`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsOrderByUnrelated__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsGroupBy

          public boolean supportsGroupBy()
                                  throws SQLException

      Is some form of "GROUP BY" clause supported?
      Specified by:
      [`supportsGroupBy`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsGroupBy__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsGroupByUnrelated

          public boolean supportsGroupByUnrelated()
                                           throws SQLException

      Can a "GROUP BY" clause use columns not in the SELECT?
      Specified by:
      [`supportsGroupByUnrelated`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsGroupByUnrelated__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsGroupByBeyondSelect

          public boolean supportsGroupByBeyondSelect()
                                              throws SQLException

      Can a "GROUP BY" clause add columns not in the SELECT provided it specifies all the columns in the SELECT?
      Specified by:
      [`supportsGroupByBeyondSelect`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsGroupByBeyondSelect__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsLikeEscapeClause

          public boolean supportsLikeEscapeClause()
                                           throws SQLException

      Is the escape character in "LIKE" clauses supported? A JDBC compliant driver always returns true.
      Specified by:
      [`supportsLikeEscapeClause`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsLikeEscapeClause__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsMultipleResultSets

          public boolean supportsMultipleResultSets()
                                             throws SQLException

      Are multiple ResultSets from a single execute supported?
      Specified by:
      [`supportsMultipleResultSets`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsMultipleResultSets__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsMultipleTransactions

          public boolean supportsMultipleTransactions()
                                               throws SQLException

      Can we have multiple transactions open at once (on different connections)?
      Specified by:
      [`supportsMultipleTransactions`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsMultipleTransactions__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsNonNullableColumns

          public boolean supportsNonNullableColumns()
                                             throws SQLException

      Can columns be defined as non-nullable? A JDBC compliant driver always returns true.
      Specified by:
      [`supportsNonNullableColumns`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsNonNullableColumns__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsMinimumSQLGrammar

          public boolean supportsMinimumSQLGrammar()
                                            throws SQLException

      Is the ODBC Minimum SQL grammar supported? All JDBC compliant drivers must return true.
      Specified by:
      [`supportsMinimumSQLGrammar`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsMinimumSQLGrammar__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsCoreSQLGrammar

          public boolean supportsCoreSQLGrammar()
                                         throws SQLException

      Is the ODBC Core SQL grammar supported?
      Specified by:
      [`supportsCoreSQLGrammar`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsCoreSQLGrammar__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsExtendedSQLGrammar

          public boolean supportsExtendedSQLGrammar()
                                             throws SQLException

      Is the ODBC Extended SQL grammar supported?
      Specified by:
      [`supportsExtendedSQLGrammar`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsExtendedSQLGrammar__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsANSI92EntryLevelSQL

          public boolean supportsANSI92EntryLevelSQL()
                                              throws SQLException

      Is the ANSI92 entry level SQL grammar supported? All JDBC compliant drivers must return true.
      Specified by:
      [`supportsANSI92EntryLevelSQL`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsANSI92EntryLevelSQL__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsANSI92IntermediateSQL

          public boolean supportsANSI92IntermediateSQL()
                                                throws SQLException

      Is the ANSI92 intermediate SQL grammar supported?
      Specified by:
      [`supportsANSI92IntermediateSQL`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsANSI92IntermediateSQL__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsANSI92FullSQL

          public boolean supportsANSI92FullSQL()
                                        throws SQLException

      Is the ANSI92 full SQL grammar supported?
      Specified by:
      [`supportsANSI92FullSQL`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsANSI92FullSQL__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsIntegrityEnhancementFacility

          public boolean supportsIntegrityEnhancementFacility()
                                                       throws SQLException

      Is the SQL Integrity Enhancement Facility supported?
      Specified by:
      [`supportsIntegrityEnhancementFacility`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsIntegrityEnhancementFacility__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsOuterJoins

          public boolean supportsOuterJoins()
                                     throws SQLException

      Is some form of outer join supported?
      Specified by:
      [`supportsOuterJoins`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsOuterJoins__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsFullOuterJoins

          public boolean supportsFullOuterJoins()
                                         throws SQLException

      Are full nested outer joins supported?
      Specified by:
      [`supportsFullOuterJoins`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsFullOuterJoins__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsLimitedOuterJoins

          public boolean supportsLimitedOuterJoins()
                                            throws SQLException

      Is there limited support for outer joins? (This will be true if supportFullOuterJoins is true.)
      Specified by:
      [`supportsLimitedOuterJoins`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsLimitedOuterJoins__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSchemaTerm

          public String getSchemaTerm()
                               throws SQLException

      What's the database vendor's preferred term for "schema"?
      Specified by:
      [`getSchemaTerm`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getSchemaTerm__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the vendor term

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getProcedureTerm

          public String getProcedureTerm()
                                  throws SQLException

      What's the database vendor's preferred term for "procedure"?
      Specified by:
      [`getProcedureTerm`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getProcedureTerm__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the vendor term

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getCatalogTerm

          public String getCatalogTerm()
                                throws SQLException

      What's the database vendor's preferred term for "catalog"?
      Specified by:
      [`getCatalogTerm`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getCatalogTerm__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the vendor term

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isCatalogAtStart

          public boolean isCatalogAtStart()
                                   throws SQLException

      Does a catalog appear at the start of a qualified table name? (Otherwise it appears at the end)
      Specified by:
      [`isCatalogAtStart`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#isCatalogAtStart__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if it appears at the start

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getCatalogSeparator

          public String getCatalogSeparator()
                                     throws SQLException

      What's the separator between catalog and table name?
      Specified by:
      [`getCatalogSeparator`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getCatalogSeparator__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the separator string

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsSchemasInDataManipulation

          public boolean supportsSchemasInDataManipulation()
                                                    throws SQLException

      Can a schema name be used in a data manipulation statement?
      Specified by:
      [`supportsSchemasInDataManipulation`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsSchemasInDataManipulation__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsSchemasInProcedureCalls

          public boolean supportsSchemasInProcedureCalls()
                                                  throws SQLException

      Can a schema name be used in a procedure call statement?
      Specified by:
      [`supportsSchemasInProcedureCalls`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsSchemasInProcedureCalls__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsSchemasInTableDefinitions

          public boolean supportsSchemasInTableDefinitions()
                                                    throws SQLException

      Can a schema name be used in a table definition statement?
      Specified by:
      [`supportsSchemasInTableDefinitions`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsSchemasInTableDefinitions__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsSchemasInIndexDefinitions

          public boolean supportsSchemasInIndexDefinitions()
                                                    throws SQLException

      Can a schema name be used in an index definition statement?
      Specified by:
      [`supportsSchemasInIndexDefinitions`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsSchemasInIndexDefinitions__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsSchemasInPrivilegeDefinitions

          public boolean supportsSchemasInPrivilegeDefinitions()
                                                        throws SQLException

      Can a schema name be used in a privilege definition statement?
      Specified by:
      [`supportsSchemasInPrivilegeDefinitions`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsSchemasInPrivilegeDefinitions__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsCatalogsInDataManipulation

          public boolean supportsCatalogsInDataManipulation()
                                                     throws SQLException

      Can a catalog name be used in a data manipulation statement?
      Specified by:
      [`supportsCatalogsInDataManipulation`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsCatalogsInDataManipulation__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsCatalogsInProcedureCalls

          public boolean supportsCatalogsInProcedureCalls()
                                                   throws SQLException

      Can a catalog name be used in a procedure call statement?
      Specified by:
      [`supportsCatalogsInProcedureCalls`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsCatalogsInProcedureCalls__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsCatalogsInTableDefinitions

          public boolean supportsCatalogsInTableDefinitions()
                                                     throws SQLException

      Can a catalog name be used in a table definition statement?
      Specified by:
      [`supportsCatalogsInTableDefinitions`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsCatalogsInTableDefinitions__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsCatalogsInIndexDefinitions

          public boolean supportsCatalogsInIndexDefinitions()
                                                     throws SQLException

      Can a catalog name be used in a index definition statement?
      Specified by:
      [`supportsCatalogsInIndexDefinitions`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsCatalogsInIndexDefinitions__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsCatalogsInPrivilegeDefinitions

          public boolean supportsCatalogsInPrivilegeDefinitions()
                                                         throws SQLException

      Can a catalog name be used in a privilege definition statement?
      Specified by:
      [`supportsCatalogsInPrivilegeDefinitions`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsCatalogsInPrivilegeDefinitions__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsPositionedDelete

          public boolean supportsPositionedDelete()
                                           throws SQLException

      Is positioned DELETE supported? NOTE: Though Oracle supports positional delete through the use of ROWID positional delete as specified by SQLJ92 standard is not supported which is being followed by JDBC 2.1 API Spec.
      Specified by:
      [`supportsPositionedDelete`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsPositionedDelete__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      false

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsPositionedUpdate

          public boolean supportsPositionedUpdate()
                                           throws SQLException

      Is positioned UPDATE supported? NOTE: Though Oracle supports positional updates through the use of ROWID positional updates as specified by SQLJ92 standard is not supported which is being followed by JDBC 2.1 API Spec.
      Specified by:
      [`supportsPositionedUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsPositionedUpdate__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      false

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsSelectForUpdate

          public boolean supportsSelectForUpdate()
                                          throws SQLException

      Is SELECT for UPDATE supported?
      Specified by:
      [`supportsSelectForUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsSelectForUpdate__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsStoredProcedures

          public boolean supportsStoredProcedures()
                                           throws SQLException

      Are stored procedure calls using the stored procedure escape syntax supported?
      Specified by:
      [`supportsStoredProcedures`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsStoredProcedures__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsSubqueriesInComparisons

          public boolean supportsSubqueriesInComparisons()
                                                  throws SQLException

      Are subqueries in comparison expressions supported? A JDBC compliant driver always returns true.
      Specified by:
      [`supportsSubqueriesInComparisons`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsSubqueriesInComparisons__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsSubqueriesInExists

          public boolean supportsSubqueriesInExists()
                                             throws SQLException

      Are subqueries in exists expressions supported? A JDBC compliant driver always returns true.
      Specified by:
      [`supportsSubqueriesInExists`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsSubqueriesInExists__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsSubqueriesInIns

          public boolean supportsSubqueriesInIns()
                                          throws SQLException

      Are subqueries in "in" statements supported? A JDBC compliant driver always returns true.
      Specified by:
      [`supportsSubqueriesInIns`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsSubqueriesInIns__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsSubqueriesInQuantifieds

          public boolean supportsSubqueriesInQuantifieds()
                                                  throws SQLException

      Are subqueries in quantified expressions supported? A JDBC compliant driver always returns true.
      Specified by:
      [`supportsSubqueriesInQuantifieds`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsSubqueriesInQuantifieds__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsCorrelatedSubqueries

          public boolean supportsCorrelatedSubqueries()
                                               throws SQLException

      Are correlated subqueries supported? A JDBC compliant driver always returns true.
      Specified by:
      [`supportsCorrelatedSubqueries`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsCorrelatedSubqueries__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsUnion

          public boolean supportsUnion()
                                throws SQLException

      Is SQL UNION supported?
      Specified by:
      [`supportsUnion`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsUnion__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsUnionAll

          public boolean supportsUnionAll()
                                   throws SQLException

      Is SQL UNION ALL supported?
      Specified by:
      [`supportsUnionAll`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsUnionAll__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsOpenCursorsAcrossCommit

          public boolean supportsOpenCursorsAcrossCommit()
                                                  throws SQLException

      Can cursors remain open across commits?
      Specified by:
      [`supportsOpenCursorsAcrossCommit`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsOpenCursorsAcrossCommit__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `Connection#disableAutoClose`

    <!-- -->

    - #### supportsOpenCursorsAcrossRollback

          public boolean supportsOpenCursorsAcrossRollback()
                                                    throws SQLException

      Can cursors remain open across rollbacks?
      Specified by:
      [`supportsOpenCursorsAcrossRollback`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsOpenCursorsAcrossRollback__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `Connection#disableAutoClose`

    <!-- -->

    - #### supportsOpenStatementsAcrossCommit

          public boolean supportsOpenStatementsAcrossCommit()
                                                     throws SQLException

      Can statements remain open across commits?
      Specified by:
      [`supportsOpenStatementsAcrossCommit`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsOpenStatementsAcrossCommit__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `Connection#disableAutoClose`

    <!-- -->

    - #### supportsOpenStatementsAcrossRollback

          public boolean supportsOpenStatementsAcrossRollback()
                                                       throws SQLException

      Can statements remain open across rollbacks?
      Specified by:
      [`supportsOpenStatementsAcrossRollback`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsOpenStatementsAcrossRollback__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `Connection#disableAutoClose`

    <!-- -->

    - #### getMaxBinaryLiteralLength

          public int getMaxBinaryLiteralLength()
                                        throws SQLException

      How many hex characters can you have in an inline binary literal?
      Specified by:
      [`getMaxBinaryLiteralLength`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxBinaryLiteralLength__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max literal length

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxCharLiteralLength

          public int getMaxCharLiteralLength()
                                      throws SQLException

      What's the max length for a character literal?
      Specified by:
      [`getMaxCharLiteralLength`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxCharLiteralLength__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max literal length

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getIdentifierLength

          protected int getIdentifierLength()
                                     throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxColumnNameLength

          public int getMaxColumnNameLength()
                                     throws SQLException

      What's the limit on column name length?
      Specified by:
      [`getMaxColumnNameLength`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxColumnNameLength__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max literal length

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxColumnsInGroupBy

          public int getMaxColumnsInGroupBy()
                                     throws SQLException

      What's the maximum number of columns in a "GROUP BY" clause?
      Specified by:
      [`getMaxColumnsInGroupBy`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxColumnsInGroupBy__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max number of columns

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxColumnsInIndex

          public int getMaxColumnsInIndex()
                                   throws SQLException

      What's the maximum number of columns allowed in an index?
      Specified by:
      [`getMaxColumnsInIndex`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxColumnsInIndex__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max columns

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxColumnsInOrderBy

          public int getMaxColumnsInOrderBy()
                                     throws SQLException

      What's the maximum number of columns in an "ORDER BY" clause?
      Specified by:
      [`getMaxColumnsInOrderBy`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxColumnsInOrderBy__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max columns

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxColumnsInSelect

          public int getMaxColumnsInSelect()
                                    throws SQLException

      What's the maximum number of columns in a "SELECT" list?
      Specified by:
      [`getMaxColumnsInSelect`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxColumnsInSelect__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max columns

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxColumnsInTable

          public int getMaxColumnsInTable()
                                   throws SQLException

      What's maximum number of columns in a table?
      Specified by:
      [`getMaxColumnsInTable`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxColumnsInTable__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max columns

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxConnections

          public int getMaxConnections()
                                throws SQLException

      How many active connections can we have at a time to this database?
      Specified by:
      [`getMaxConnections`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxConnections__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max connections

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxCursorNameLength

          public int getMaxCursorNameLength()
                                     throws SQLException

      What's the maximum cursor name length?
      Specified by:
      [`getMaxCursorNameLength`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxCursorNameLength__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max cursor name length in bytes

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxIndexLength

          public int getMaxIndexLength()
                                throws SQLException

      What's the maximum length of an index (in bytes)?
      Specified by:
      [`getMaxIndexLength`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxIndexLength__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max index length in bytes

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxSchemaNameLength

          public int getMaxSchemaNameLength()
                                     throws SQLException

      What's the maximum length allowed for a schema name?
      Specified by:
      [`getMaxSchemaNameLength`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxSchemaNameLength__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max name length in bytes

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxProcedureNameLength

          public int getMaxProcedureNameLength()
                                        throws SQLException

      What's the maximum length of a procedure name?
      Specified by:
      [`getMaxProcedureNameLength`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxProcedureNameLength__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max name length in bytes

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxCatalogNameLength

          public int getMaxCatalogNameLength()
                                      throws SQLException

      What's the maximum length of a catalog name?
      Specified by:
      [`getMaxCatalogNameLength`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxCatalogNameLength__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max name length in bytes

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxRowSize

          public int getMaxRowSize()
                            throws SQLException

      What's the maximum length of a single row?
      Specified by:
      [`getMaxRowSize`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxRowSize__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max row size in bytes

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### doesMaxRowSizeIncludeBlobs

          public boolean doesMaxRowSizeIncludeBlobs()
                                             throws SQLException

      Did getMaxRowSize() include LONGVARCHAR and LONGVARBINARY blobs?
      Specified by:
      [`doesMaxRowSizeIncludeBlobs`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#doesMaxRowSizeIncludeBlobs__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxStatementLength

          public int getMaxStatementLength()
                                    throws SQLException

      What's the maximum length of a SQL statement?
      Specified by:
      [`getMaxStatementLength`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxStatementLength__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max length in bytes

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxStatements

          public int getMaxStatements()
                               throws SQLException

      How many active statements can we have open at one time to this database?
      Specified by:
      [`getMaxStatements`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxStatements__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the maximum

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxTableNameLength

          public int getMaxTableNameLength()
                                    throws SQLException

      What's the maximum length of a table name?
      Specified by:
      [`getMaxTableNameLength`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxTableNameLength__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max name length in bytes

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxTablesInSelect

          public int getMaxTablesInSelect()
                                   throws SQLException

      What's the maximum number of tables in a SELECT?
      Specified by:
      [`getMaxTablesInSelect`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxTablesInSelect__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the maximum

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxUserNameLength

          public int getMaxUserNameLength()
                                   throws SQLException

      What's the maximum length of a user name?
      Specified by:
      [`getMaxUserNameLength`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getMaxUserNameLength__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      max name length in bytes

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDefaultTransactionIsolation

          public int getDefaultTransactionIsolation()
                                             throws SQLException

      What's the database's default transaction isolation level? The values are defined in java.sql.Connection.
      Specified by:
      [`getDefaultTransactionIsolation`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getDefaultTransactionIsolation__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the default isolation level

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)

    <!-- -->

    - #### supportsTransactions

          public boolean supportsTransactions()
                                       throws SQLException

      Are transactions supported? If not, commit is a noop and the isolation level is TRANSACTION_NONE.
      Specified by:
      [`supportsTransactions`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsTransactions__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if transactions are supported

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsTransactionIsolationLevel

          public boolean supportsTransactionIsolationLevel(int level)
                                                    throws SQLException

      Does the database support the given transaction isolation level?
      Specified by:
      [`supportsTransactionIsolationLevel`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsTransactionIsolationLevel_int_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `level` - the values are defined in java.sql.Connection

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)

    <!-- -->

    - #### supportsDataDefinitionAndDataManipulationTransactions

          public boolean supportsDataDefinitionAndDataManipulationTransactions()
                                                                        throws SQLException

      Are both data definition and data manipulation statements within a transaction supported?
      Specified by:
      [`supportsDataDefinitionAndDataManipulationTransactions`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsDataDefinitionAndDataManipulationTransactions__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsDataManipulationTransactionsOnly

          public boolean supportsDataManipulationTransactionsOnly()
                                                           throws SQLException

      Are only data manipulation statements within a transaction supported?
      Specified by:
      [`supportsDataManipulationTransactionsOnly`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsDataManipulationTransactionsOnly__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### dataDefinitionCausesTransactionCommit

          public boolean dataDefinitionCausesTransactionCommit()
                                                        throws SQLException

      Does a data definition statement within a transaction force the transaction to commit?
      Specified by:
      [`dataDefinitionCausesTransactionCommit`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#dataDefinitionCausesTransactionCommit__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### dataDefinitionIgnoredInTransactions

          public boolean dataDefinitionIgnoredInTransactions()
                                                      throws SQLException

      Is a data definition statement within a transaction ignored?
      Specified by:
      [`dataDefinitionIgnoredInTransactions`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#dataDefinitionIgnoredInTransactions__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if so

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getProcedures

          public ResultSet getProcedures(String catalog,
                                         String schemaPattern,
                                         String procedureNamePattern)
                                  throws SQLException

      Get a description of stored procedures available in a catalog.
      Only procedure descriptions matching the schema and procedure name criteria are returned. They are ordered by PROCEDURE_SCHEM, and PROCEDURE_NAME.

      Each procedure description has the the following columns:

      1.  **PROCEDURE_CAT** String =\> procedure catalog (may be null)
      2.  **PROCEDURE_SCHEM** String =\> procedure schema (may be null)
      3.  **PROCEDURE_NAME** String =\> procedure name
      4.  reserved for future use
      5.  reserved for future use
      6.  reserved for future use
      7.  **REMARKS** String =\> explanatory comment on the procedure
      8.  **PROCEDURE_TYPE** short =\> kind of procedure:
          - procedureResultUnknown - May return a result
          - procedureNoResult - Does not return a result
          - procedureReturnsResult - Returns a result

      Specified by:
      [`getProcedures`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getProcedures_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; "" retrieves those without a catalog; null means drop catalog name from the selection criteria

      `schemaPattern` - a schema name pattern; "" retrieves those without a schema

      `procedureNamePattern` - a procedure name pattern

      Returns:
      ResultSet each row is a procedure description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `getSearchStringEscape()`

    <!-- -->

    - #### getProcedureColumns

          public ResultSet getProcedureColumns(String catalog,
                                               String schemaPattern,
                                               String procedureNamePattern,
                                               String columnNamePattern)
                                        throws SQLException

      Get a description of a catalog's stored procedure parameters and result columns.
      Only descriptions matching the schema, procedure and parameter name criteria are returned. They are ordered by PROCEDURE_SCHEM and PROCEDURE_NAME. Within this, the return value, if any, is first. Next are the parameter descriptions in call order. The column descriptions follow in column number order.

      Each row in the ResultSet is a parameter desription or column description with the following fields:

      1.  **PROCEDURE_CAT** String =\> procedure catalog (may be null) Interpreted as the Oracle Package name.
      2.  **PROCEDURE_SCHEM** String =\> procedure schema (may be null)
      3.  **PROCEDURE_NAME** String =\> procedure name
      4.  **COLUMN_NAME** String =\> column/parameter name
      5.  **COLUMN_TYPE** Short =\> kind of column/parameter:
          - procedureColumnUnknown - nobody knows
          - procedureColumnIn - IN parameter
          - procedureColumnInOut - INOUT parameter
          - procedureColumnOut - OUT parameter
          - procedureColumnReturn - procedure return value
          - procedureColumnResult - result column in ResultSet
      6.  **DATA_TYPE** short =\> SQL type from java.sql.Types
      7.  **TYPE_NAME** String =\> SQL type name
      8.  **PRECISION** int =\> precision
      9.  **LENGTH** int =\> length in bytes of data
      10. **SCALE** short =\> scale
      11. **RADIX** short =\> radix
      12. **NULLABLE** short =\> can it contain NULL?
          - procedureNoNulls - does not allow NULL values
          - procedureNullable - allows NULL values
          - procedureNullableUnknown - nullability unknown
      13. **REMARKS** String =\> comment describing parameter/column

      **Note:** Some databases may not return the column descriptions for a procedure. Additional columns beyond REMARKS can be defined by the database. These additional columns **MUST** be accessed by name, not by index.

      **Oracle Specific:**

      The catalog argument is taken to mean a package name. Note that this is not a pattern and wildcards are not supported.

      Database synonyms may be defined (amoung other things) for a package, for an unpackaged procedure or for a synonym. The combination of synonyms and wildcards in the schemaPattern and procedureNamePattern is supported in a limited way due to complexity and performace issues.

      If the schemaPattern does not contain wildcards and the catalog argument is not null and not empty, the values are taken as either a schema + package name or a schema + synonym for a package. If it is a synonym, it will be resolved perhaps through multiple levels of synonyms and the search for the procedureNamePattern and columnNamePatten will be conducted in the resulting package.

      If the catalog is null and both the schemaNamePattern and procedureNamePattern do not contain wildcards, the values are taken as either a schema + procedureName or a schema + synonym. If it is a synonym it will be resolved perhaps through multiple levels of synonyms and the search for the columnNamePatten will be conducted in the resulting procedure

      Specified by:
      [`getProcedureColumns`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getProcedureColumns_java_lang_String_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; "" retrieves those without a catalog; null means drop catalog name from the selection criteria

      `schemaPattern` - a schema name pattern; "" retrieves those without a schema

      `procedureNamePattern` - a procedure name pattern

      `columnNamePattern` - a column name pattern

      Returns:
      ResultSet each row is a stored procedure parameter or column description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `getSearchStringEscape()`

    <!-- -->

    - #### getFunctionColumns

          public ResultSet getFunctionColumns(String catalog,
                                              String schemaPattern,
                                              String functionNamePattern,
                                              String columnNamePattern)
                                       throws SQLException

      Retrieves a description of the given catalog's system or user function parameters and return type.
      Only descriptions matching the schema, function and parameter name criteria are returned. They are ordered by `FUNCTION_CAT`, `FUNCTION_SCHEM`, `FUNCTION_NAME` and `SPECIFIC_ NAME`. Within this, the return value, if any, is first. Next are the parameter descriptions in call order. The column descriptions follow in column number order.

      Each row in the `ResultSet` is a parameter description, column description or return type description with the following fields:

      1.  **FUNCTION_CAT** String =\> function catalog (may be `null`)
      2.  **FUNCTION_SCHEM** String =\> function schema (may be `null`)
      3.  **FUNCTION_NAME** String =\> function name. This is the name used to invoke the function
      4.  **COLUMN_NAME** String =\> column/parameter name
      5.  **COLUMN_TYPE** Short =\> kind of column/parameter:
          - functionColumnUnknown - nobody knows
          - functionColumnIn - IN parameter
          - functionColumnInOut - INOUT parameter
          - functionColumnOut - OUT parameter
          - functionColumnReturn - function return value
          - functionColumnResult - Indicates that the parameter or column is a column in the `ResultSet`
      6.  **DATA_TYPE** int =\> SQL type from java.sql.Types
      7.  **TYPE_NAME** String =\> SQL type name, for a UDT type the type name is fully qualified
      8.  **PRECISION** int =\> precision
      9.  **LENGTH** int =\> length in bytes of data
      10. **SCALE** short =\> scale - null is returned for data types where SCALE is not applicable.
      11. **RADIX** short =\> radix
      12. **NULLABLE** short =\> can it contain NULL.
          - functionNoNulls - does not allow NULL values
          - functionNullable - allows NULL values
          - functionNullableUnknown - nullability unknown
      13. **REMARKS** String =\> comment describing column/parameter
      14. **CHAR_OCTET_LENGTH** int =\> the maximum length of binary and character based parameters or columns. For any other datatype the returned value is a NULL
      15. **ORDINAL_POSITION** int =\> the ordinal position, starting from 1, for the input and output parameters. A value of 0 is returned if this row describes the function's return value. For result set columns, it is the ordinal position of the column in the result set starting from 1.
      16. **IS_NULLABLE** String =\> ISO rules are used to determine the nullability for a parameter or column.
          - YES --- if the parameter or column can include NULLs
          - NO --- if the parameter or column cannot include NULLs
          - empty string --- if the nullability for the parameter or column is unknown
      17. **SPECIFIC_NAME** String =\> the name which uniquely identifies this function within its schema. This is a user specified, or DBMS generated, name that may be different then the `FUNCTION_NAME` for example with overload functions

      The PRECISION column represents the specified column size for the given parameter or column. For numeric data, this is the maximum precision. For character data, this is the length in characters. For datetime datatypes, this is the length in characters of the String representation (assuming the maximum allowed precision of the fractional seconds component). For binary data, this is the length in bytes. For the ROWID datatype, this is the length in bytes. Null is returned for data types where the column size is not applicable.

      **Note:** If the user defined function in the database has failed to compile, this method returns an empty resultset.

      Specified by:
      [`getFunctionColumns`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getFunctionColumns_java_lang_String_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; must match the catalog name as it is stored in the database; "" retrieves those without a catalog; `null` means that the catalog name should not be used to narrow the search

      `schemaPattern` - a schema name pattern; must match the schema name as it is stored in the database; "" retrieves those without a schema; `null` means that the schema name should not be used to narrow the search

      `functionNamePattern` - a procedure name pattern; must match the function name as it is stored in the database

      `columnNamePattern` - a parameter name pattern; must match the parameter or column name as it is stored in the database

      Returns:
      `ResultSet` - each row describes a user function parameter, column or return type

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      1.6

      See Also:
      `getSearchStringEscape()`

    <!-- -->

    - #### getTables

          public ResultSet getTables(String catalog,
                                     String schemaPattern,
                                     String tableNamePattern,
                                     String[] types)
                              throws SQLException

      Get a description of tables available in a catalog.
      Only table descriptions matching the catalog, schema, table name and type criteria are returned. They are ordered by TABLE_TYPE, TABLE_SCHEM and TABLE_NAME.

      Each table description has the following columns:

      1.  **TABLE_CAT** String =\> table catalog (may be null)
      2.  **TABLE_SCHEM** String =\> table schema (may be null)
      3.  **TABLE_NAME** String =\> table name
      4.  **TABLE_TYPE** String =\> table type. Typical types are "TABLE", "VIEW", "SYSTEM TABLE", "GLOBAL TEMPORARY", "LOCAL TEMPORARY", "ALIAS", "SYNONYM".
      5.  **TABLE_REMARKS** String =\> explanatory comment on the table

      **Note:** Some databases may not return information for all tables.

      Specified by:
      [`getTables`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getTables_java_lang_String_java_lang_String_java_lang_String_java_lang_String_A_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; "" retrieves those without a catalog; null means drop catalog name from the selection criteria

      `schemaPattern` - a schema name pattern; "" retrieves those without a schema

      `tableNamePattern` - a table name pattern

      `types` - a list of table types to include; null returns all types

      Returns:
      ResultSet each row is a table description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `getSearchStringEscape()`

    <!-- -->

    - #### getSchemas

          public ResultSet getSchemas()
                               throws SQLException

      Get the schema names available in this database. The results are ordered by schema name.
      The schema columns are:

      1.  **TABLE_CATALOG** String =\> catalog name always `null`

      Specified by:
      [`getSchemas`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getSchemas__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      ResultSet each row has a single String column that is a schema name

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getCatalogs

          public ResultSet getCatalogs()
                                throws SQLException

      Get the catalog names available in this database. The results are ordered by catalog name.
      The catalog column is:

      1.  **TABLE_CAT** String =\> catalog name

      Specified by:
      [`getCatalogs`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getCatalogs__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      ResultSet each row has a single String column that is a catalog name

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getTableTypes

          public ResultSet getTableTypes()
                                  throws SQLException

      Get the table types available in this database. The results are ordered by table type.
      The table type is:

      1.  **TABLE_TYPE** String =\> table type. Typical types are "TABLE", "VIEW", "SYSTEM TABLE", "GLOBAL TEMPORARY", "LOCAL TEMPORARY", "ALIAS", "SYNONYM".

      Specified by:
      [`getTableTypes`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getTableTypes__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      ResultSet each row has a single String column that is a table type

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getColumns

          public ResultSet getColumns(String catalog,
                                      String schemaPattern,
                                      String tableNamePattern,
                                      String columnNamePattern)
                               throws SQLException

      Get a description of table columns available in a catalog.
      Only column descriptions matching the catalog, schema, table and column name criteria are returned. They are ordered by TABLE_SCHEM, TABLE_NAME and ORDINAL_POSITION.

      Each column description has the following columns:

      1.  **TABLE_CAT** String =\> table catalog (may be null)
      2.  **TABLE_SCHEM** String =\> table schema (may be null)
      3.  **TABLE_NAME** String =\> table name
      4.  **COLUMN_NAME** String =\> column name
      5.  **DATA_TYPE** short =\> SQL type from java.sql.Types
      6.  **TYPE_NAME** String =\> Data source dependent type name
      7.  **COLUMN_SIZE** int =\> column size. For char or date types this is the maximum number of characters, for numeric or decimal types this is precision.
      8.  **BUFFER_LENGTH** is not used.
      9.  **DECIMAL_DIGITS** int =\> the number of fractional digits
      10. **NUM_PREC_RADIX** int =\> Radix (typically either 10 or 2)
      11. **NULLABLE** int =\> is NULL allowed?
          - columnNoNulls - might not allow NULL values
          - columnNullable - definitely allows NULL values
          - columnNullableUnknown - nullability unknown
      12. **REMARKS** String =\> comment describing column (may be null)
      13. **COLUMN_DEF** String =\> default value (may be null)
      14. **SQL_DATA_TYPE** int =\> unused
      15. **SQL_DATETIME_SUB** int =\> unused
      16. **CHAR_OCTET_LENGTH** int =\> for char types the maximum number of bytes in the column
      17. **ORDINAL_POSITION** int =\> index of column in table (starting at 1)
      18. **IS_NULLABLE** String =\> "NO" means column definitely does not allow NULL values; "YES" means the column might allow NULL values. An empty string means nobody knows.
      19. **SCOPE_CATLOG** String =\> catalog of table that is the scope of a reference attribute (`null` if DATA_TYPE isn't REF)
      20. **SCOPE_SCHEMA** String =\> schema of table that is the scope of a reference attribute (`null` if the DATA_TYPE isn't REF)
      21. **SCOPE_TABLE** String =\> table name that this the scope of a reference attribure (`null` if the DATA_TYPE isn't REF)
      22. **SOURCE_DATA_TYPE** short =\> source type of a distinct type or user-generated Ref type, SQL type from java.sql.Types (`null` if DATA_TYPE isn't DISTINCT or user-generated REF)
      23. **IS_AUTOINCREMENT** String =\> Indicates whether this column is auto incremented
          - YES --- if the column is auto incremented
          - NO --- if the column is not auto incremented
          - empty string --- if it cannot be determined whether the column is auto incremented parameter is unknown

      Specified by:
      [`getColumns`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getColumns_java_lang_String_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; "" retrieves those without a catalog; null means drop catalog name from the selection criteria

      `schemaPattern` - a schema name pattern; "" retrieves those without a schema

      `tableNamePattern` - a table name pattern

      `columnNamePattern` - a column name pattern

      Returns:
      ResultSet each row is a column description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `getSearchStringEscape()`

    <!-- -->

    - #### getColumnPrivileges

          public ResultSet getColumnPrivileges(String catalog,
                                               String schemaPattern,
                                               String tableNamePattern,
                                               String columnNamePattern)
                                        throws SQLException

      Get a description of the access rights for a table's columns.
      Only privileges matching the column name criteria are returned. They are ordered by COLUMN_NAME and PRIVILEGE.

      Each privilige description has the following columns:

      1.  **TABLE_CAT** String =\> table catalog (may be null)
      2.  **TABLE_SCHEM** String =\> table schema (may be null)
      3.  **TABLE_NAME** String =\> table name
      4.  **COLUMN_NAME** String =\> column name
      5.  **GRANTOR** =\> grantor of access (may be null)
      6.  **GRANTEE** String =\> grantee of access
      7.  **PRIVILEGE** String =\> name of access (SELECT, INSERT, UPDATE, REFRENCES, ...)
      8.  **IS_GRANTABLE** String =\> "YES" if grantee is permitted to grant to others; "NO" if not; null if unknown

      Specified by:
      [`getColumnPrivileges`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getColumnPrivileges_java_lang_String_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; "" retrieves those without a catalog; null means drop catalog name from the selection criteria

      `schemaPattern` - a schema name; "" retrieves those without a schema

      `tableNamePattern` - a table name

      `columnNamePattern` - a column name pattern

      Returns:
      ResultSet each row is a column privilege description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `getSearchStringEscape()`

    <!-- -->

    - #### getTablePrivileges

          public ResultSet getTablePrivileges(String catalog,
                                              String schemaPattern,
                                              String tableNamePattern)
                                       throws SQLException

      Get a description of the access rights for each table available in a catalog.
      Only privileges matching the schema and table name criteria are returned. They are ordered by TABLE_SCHEM, TABLE_NAME, and PRIVILEGE.

      Each privilige description has the following columns:

      1.  **TABLE_CAT** String =\> table catalog (may be null)
      2.  **TABLE_SCHEM** String =\> table schema (may be null)
      3.  **TABLE_NAME** String =\> table name
      4.  **COLUMN_NAME** String =\> column name
      5.  **GRANTOR** =\> grantor of access (may be null)
      6.  **GRANTEE** String =\> grantee of access
      7.  **PRIVILEGE** String =\> name of access (SELECT, INSERT, UPDATE, REFRENCES, ...)
      8.  **IS_GRANTABLE** String =\> "YES" if grantee is permitted to grant to others; "NO" if not; null if unknown

      Specified by:
      [`getTablePrivileges`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getTablePrivileges_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; "" retrieves those without a catalog; null means drop catalog name from the selection criteria

      `schemaPattern` - a schema name pattern; "" retrieves those without a schema

      `tableNamePattern` - a table name pattern

      Returns:
      ResultSet each row is a table privilege description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `getSearchStringEscape()`

    <!-- -->

    - #### getBestRowIdentifier

          public ResultSet getBestRowIdentifier(String catalog,
                                                String schema,
                                                String table,
                                                int scope,
                                                boolean nullable)
                                         throws SQLException

      Get a description of a table's optimal set of columns that uniquely identifies a row. They are ordered by SCOPE.
      Each column description has the following columns:

      1.  **SCOPE** short =\> actual scope of result
          - bestRowTemporary - very temporary, while using row
          - bestRowTransaction - valid for remainder of current transaction
          - bestRowSession - valid for remainder of current session
      2.  **COLUMN_NAME** String =\> column name
      3.  **DATA_TYPE** short =\> SQL data type from java.sql.Types
      4.  **TYPE_NAME** String =\> Data source dependent type name
      5.  **COLUMN_SIZE** int =\> precision
      6.  **BUFFER_LENGTH** int =\> not used
      7.  **DECIMAL_DIGITS** short =\> scale
      8.  **PSEUDO_COLUMN** short =\> is this a pseudo column like an Oracle ROWID
          - bestRowUnknown - may or may not be pseudo column
          - bestRowNotPseudo - is NOT a pseudo column
          - bestRowPseudo - is a pseudo column

      Specified by:
      [`getBestRowIdentifier`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getBestRowIdentifier_java_lang_String_java_lang_String_java_lang_String_int_boolean_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; "" retrieves those without a catalog; null means drop catalog name from the selection criteria

      `schema` - a schema name; "" retrieves those without a schema

      `table` - a table name

      `scope` - the scope of interest; use same values as SCOPE

      `nullable` - include columns that are nullable?

      Returns:
      ResultSet each row is a column description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getVersionColumns

          public ResultSet getVersionColumns(String catalog,
                                             String schema,
                                             String table)
                                      throws SQLException

      Get a description of a table's columns that are automatically updated when any value in a row is updated. They are unordered.
      Each column description has the following columns:

      1.  **SCOPE** short =\> is not used
      2.  **COLUMN_NAME** String =\> column name
      3.  **DATA_TYPE** short =\> SQL data type from java.sql.Types
      4.  **TYPE_NAME** String =\> Data source dependent type name
      5.  **COLUMN_SIZE** int =\> precision
      6.  **BUFFER_LENGTH** int =\> length of column value in bytes
      7.  **DECIMAL_DIGITS** short =\> scale
      8.  **PSEUDO_COLUMN** short =\> is this a pseudo column like an Oracle ROWID
          - versionColumnUnknown - may or may not be pseudo column
          - versionColumnNotPseudo - is NOT a pseudo column
          - versionColumnPseudo - is a pseudo column

      Specified by:
      [`getVersionColumns`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getVersionColumns_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; "" retrieves those without a catalog; null means drop catalog name from the selection criteria

      `schema` - a schema name; "" retrieves those without a schema

      `table` - a table name

      Returns:
      ResultSet each row is a column description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getPrimaryKeys

          public ResultSet getPrimaryKeys(String catalog,
                                          String schema,
                                          String table)
                                   throws SQLException

      Get a description of a table's primary key columns. They are ordered by COLUMN_NAME.
      Each column description has the following columns:

      1.  **TABLE_CAT** String =\> table catalog (may be null)
      2.  **TABLE_SCHEM** String =\> table schema (may be null)
      3.  **TABLE_NAME** String =\> table name
      4.  **COLUMN_NAME** String =\> column name
      5.  **KEY_SEQ** short =\> sequence number within primary key
      6.  **PK_NAME** String =\> primary key name (may be null)

      Specified by:
      [`getPrimaryKeys`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getPrimaryKeys_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; "" retrieves those without a catalog; null means drop catalog name from the selection criteria

      `schema` - a schema name pattern; "" retrieves those without a schema

      `table` - a table name

      Returns:
      ResultSet each row is a primary key column description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getImportedKeys

          public ResultSet getImportedKeys(String catalog,
                                           String schema,
                                           String table)
                                    throws SQLException

      Get a description of the primary key columns that are referenced by a table's foreign key columns (the primary keys imported by a table). They are ordered by PKTABLE_CAT, PKTABLE_SCHEM, PKTABLE_NAME, and KEY_SEQ.
      Each primary key column description has the following columns:

      1.  **PKTABLE_CAT** String =\> primary key table catalog being imported (may be null)
      2.  **PKTABLE_SCHEM** String =\> primary key table schema being imported (may be null)
      3.  **PKTABLE_NAME** String =\> primary key table name being imported
      4.  **PKCOLUMN_NAME** String =\> primary key column name being imported
      5.  **FKTABLE_CAT** String =\> foreign key table catalog (may be null)
      6.  **FKTABLE_SCHEM** String =\> foreign key table schema (may be null)
      7.  **FKTABLE_NAME** String =\> foreign key table name
      8.  **FKCOLUMN_NAME** String =\> foreign key column name
      9.  **KEY_SEQ** short =\> sequence number within foreign key
      10. **UPDATE_RULE** short =\> What happens to foreign key when primary is updated:
          - importedKeyCascade - change imported key to agree with primary key update
          - importedKeyRestrict - do not allow update of primary key if it has been imported
          - importedKeySetNull - change imported key to NULL if its primary key has been updated
      11. **DELETE_RULE** short =\> What happens to the foreign key when primary is deleted.
          - importedKeyCascade - delete rows that import a deleted key
          - importedKeyRestrict - do not allow delete of primary key if it has been imported
          - importedKeySetNull - change imported key to NULL if its primary key has been deleted
      12. **FK_NAME** String =\> foreign key name (may be null)
      13. **PK_NAME** String =\> primary key name (may be null)

      Specified by:
      [`getImportedKeys`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getImportedKeys_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; "" retrieves those without a catalog; null means drop catalog name from the selection criteria

      `schema` - a schema name pattern; "" retrieves those without a schema

      `table` - a table name

      Returns:
      ResultSet each row is a primary key column description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `getExportedKeys(java.lang.String, java.lang.String, java.lang.String)`

    <!-- -->

    - #### getExportedKeys

          public ResultSet getExportedKeys(String catalog,
                                           String schema,
                                           String table)
                                    throws SQLException

      Get a description of a foreign key columns that reference a table's primary key columns (the foreign keys exported by a table). They are ordered by FKTABLE_CAT, FKTABLE_SCHEM, FKTABLE_NAME, and KEY_SEQ.
      Each foreign key column description has the following columns:

      1.  **PKTABLE_CAT** String =\> primary key table catalog (may be null)
      2.  **PKTABLE_SCHEM** String =\> primary key table schema (may be null)
      3.  **PKTABLE_NAME** String =\> primary key table name
      4.  **PKCOLUMN_NAME** String =\> primary key column name
      5.  **FKTABLE_CAT** String =\> foreign key table catalog (may be null) being exported (may be null)
      6.  **FKTABLE_SCHEM** String =\> foreign key table schema (may be null) being exported (may be null)
      7.  **FKTABLE_NAME** String =\> foreign key table name being exported
      8.  **FKCOLUMN_NAME** String =\> foreign key column name being exported
      9.  **KEY_SEQ** short =\> sequence number within foreign key
      10. **UPDATE_RULE** short =\> What happens to foreign key when primary is updated:
          - importedKeyCascade - change imported key to agree with primary key update
          - importedKeyRestrict - do not allow update of primary key if it has been imported
          - importedKeySetNull - change imported key to NULL if its primary key has been updated
      11. **DELETE_RULE** short =\> What happens to the foreign key when primary is deleted.
          - importedKeyCascade - delete rows that import a deleted key
          - importedKeyRestrict - do not allow delete of primary key if it has been imported
          - importedKeySetNull - change imported key to NULL if its primary key has been deleted
      12. **FK_NAME** String =\> foreign key identifier (may be null)
      13. **PK_NAME** String =\> primary key identifier (may be null)

      Specified by:
      [`getExportedKeys`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getExportedKeys_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; "" retrieves those without a catalog; null means drop catalog name from the selection criteria

      `schema` - a schema name pattern; "" retrieves those without a schema

      `table` - a table name

      Returns:
      ResultSet each row is a foreign key column description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `getImportedKeys(java.lang.String, java.lang.String, java.lang.String)`

    <!-- -->

    - #### getCrossReference

          public ResultSet getCrossReference(String primaryCatalog,
                                             String primarySchema,
                                             String primaryTable,
                                             String foreignCatalog,
                                             String foreignSchema,
                                             String foreignTable)
                                      throws SQLException

      Get a description of the foreign key columns in the foreign key table that reference the primary key columns of the primary key table (describe how one table imports another's key.) This should normally return a single foreign key/primary key pair (most tables only import a foreign key from a table once.) They are ordered by FKTABLE_CAT, FKTABLE_SCHEM, FKTABLE_NAME, and KEY_SEQ.
      Each foreign key column description has the following columns:

      1.  **PKTABLE_CAT** String =\> primary key table catalog (may be null)
      2.  **PKTABLE_SCHEM** String =\> primary key table schema (may be null)
      3.  **PKTABLE_NAME** String =\> primary key table name
      4.  **PKCOLUMN_NAME** String =\> primary key column name
      5.  **FKTABLE_CAT** String =\> foreign key table catalog (may be null) being exported (may be null)
      6.  **FKTABLE_SCHEM** String =\> foreign key table schema (may be null) being exported (may be null)
      7.  **FKTABLE_NAME** String =\> foreign key table name being exported
      8.  **FKCOLUMN_NAME** String =\> foreign key column name being exported
      9.  **KEY_SEQ** short =\> sequence number within foreign key
      10. **UPDATE_RULE** short =\> What happens to foreign key when primary is updated:
          - importedKeyCascade - change imported key to agree with primary key update
          - importedKeyRestrict - do not allow update of primary key if it has been imported
          - importedKeySetNull - change imported key to NULL if its primary key has been updated
      11. **DELETE_RULE** short =\> What happens to the foreign key when primary is deleted.
          - importedKeyCascade - delete rows that import a deleted key
          - importedKeyRestrict - do not allow delete of primary key if it has been imported
          - importedKeySetNull - change imported key to NULL if its primary key has been deleted
      12. **FK_NAME** String =\> foreign key identifier (may be null)
      13. **PK_NAME** String =\> primary key identifier (may be null)

      Specified by:
      [`getCrossReference`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getCrossReference_java_lang_String_java_lang_String_java_lang_String_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `primaryCatalog` - a catalog name; "" retrieves those without a catalog; null means drop catalog name from the selection criteria

      `primarySchema` - a schema name pattern; "" retrieves those without a schema

      `primaryTable` - the table name that exports the key

      `foreignCatalog` - a catalog name; "" retrieves those without a catalog; null means drop catalog name from the selection criteria

      `foreignSchema` - a schema name pattern; "" retrieves those without a schema

      `foreignTable` - the table name that imports the key

      Returns:
      ResultSet each row is a foreign key column description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `getImportedKeys(java.lang.String, java.lang.String, java.lang.String)`

    <!-- -->

    - #### getTypeInfo

          public ResultSet getTypeInfo()
                                throws SQLException

      Get a description of all the standard SQL types supported by this database. They are ordered by DATA_TYPE and then by how closely the data type maps to the corresponding JDBC SQL type.
      Each type description has the following columns:

      1.  **TYPE_NAME** String =\> Type name
      2.  **DATA_TYPE** short =\> SQL data type from java.sql.Types
      3.  **PRECISION** int =\> maximum precision
      4.  **LITERAL_PREFIX** String =\> prefix used to quote a literal (may be null)
      5.  **LITERAL_SUFFIX** String =\> suffix used to quote a literal (may be null)
      6.  **CREATE_PARAMS** String =\> parameters used in creating the type (may be null)
      7.  **NULLABLE** short =\> can you use NULL for this type?
          - typeNoNulls - does not allow NULL values
          - typeNullable - allows NULL values
          - typeNullableUnknown - nullability unknown
      8.  **CASE_SENSITIVE** boolean=\> is it case sensitive?
      9.  **SEARCHABLE** short =\> can you use "WHERE" based on this type:
          - typePredNone - No support
          - typePredChar - Only supported with WHERE .. LIKE
          - typePredBasic - Supported except for WHERE .. LIKE
          - typeSearchable - Supported for all WHERE ..
      10. **UNSIGNED_ATTRIBUTE** boolean =\> is it unsigned?
      11. **FIXED_PREC_SCALE** boolean =\> can it be a money value?
      12. **AUTO_INCREMENT** boolean =\> can it be used for an auto-increment value?
      13. **LOCAL_TYPE_NAME** String =\> localized version of type name (may be null)
      14. **MINIMUM_SCALE** short =\> minimum scale supported
      15. **MAXIMUM_SCALE** short =\> maximum scale supported
      16. **SQL_DATA_TYPE** int =\> unused
      17. **SQL_DATETIME_SUB** int =\> unused
      18. **NUM_PREC_RADIX** int =\> usually 2 or 10

      Specified by:
      [`getTypeInfo`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getTypeInfo__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      ResultSet each row is a SQL type description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getIndexInfo

          public ResultSet getIndexInfo(String catalog,
                                        String schema,
                                        String table,
                                        boolean unique,
                                        boolean approximate)
                                 throws SQLException

      Get a description of a table's indices and statistics. They are ordered by NON_UNIQUE, TYPE, INDEX_NAME, and ORDINAL_POSITION.
      Each index column description has the following columns:

      1.  **TABLE_CAT** String =\> table catalog (may be null)
      2.  **TABLE_SCHEM** String =\> table schema (may be null)
      3.  **TABLE_NAME** String =\> table name
      4.  **NON_UNIQUE** boolean =\> Can index values be non-unique? false when TYPE is tableIndexStatistic
      5.  **INDEX_QUALIFIER** String =\> index catalog (may be null); null when TYPE is tableIndexStatistic
      6.  **INDEX_NAME** String =\> index name; null when TYPE is tableIndexStatistic
      7.  **TYPE** short =\> index type:
          - tableIndexStatistic - this identifies table statistics that are returned in conjuction with a table's index descriptions
          - tableIndexClustered - this is a clustered index
          - tableIndexHashed - this is a hashed index
          - tableIndexOther - this is some other style of index
      8.  **ORDINAL_POSITION** short =\> column sequence number within index; zero when TYPE is tableIndexStatistic
      9.  **COLUMN_NAME** String =\> column name; null when TYPE is tableIndexStatistic
      10. **ASC_OR_DESC** String =\> column sort sequence, "A" =\> ascending, "D" =\> descending, may be null if sort sequence is not supported; null when TYPE is tableIndexStatistic
      11. **CARDINALITY** int =\> When TYPE is tableIndexStatisic then this is the number of rows in the table; otherwise it is the number of unique values in the index.
      12. **PAGES** int =\> When TYPE is tableIndexStatisic then this is the number of pages used for the table, otherwise it is the number of pages used for the current index.
      13. **FILTER_CONDITION** String =\> Filter condition, if any. (may be null)

      Specified by:
      [`getIndexInfo`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getIndexInfo_java_lang_String_java_lang_String_java_lang_String_boolean_boolean_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; "" retrieves those without a catalog; null means drop catalog name from the selection criteria

      `schema` - a schema name pattern; "" retrieves those without a schema

      `table` - a table name

      `unique` - when true, return only indices for unique values; when false, return indices regardless of whether unique or not

      `approximate` - when true, result is allowed to reflect approximate or out of data values; when false, results are requested to be accurate

      Note: The schema and table names may be used internally to create a query to get further information from the database. They must conform to the Oracle schema object naming rules. Examples of valid names: last_name, horse,"MY-TEST", "EVEN THIS & THAT!"

      Returns:
      ResultSet each row is an index column description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsResultSetType

          public boolean supportsResultSetType(int type)
                                        throws SQLException

      Implements JDBC 2.0 DatabaseMetaData.supportsResultSetType. Does the database support the given result set type? This method always return true.
      Specified by:
      [`supportsResultSetType`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsResultSetType_int_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `type` - defined in `java.sql.ResultSet`

      Returns:
      true always

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      See Also:
      [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)

    <!-- -->

    - #### supportsResultSetConcurrency

          public boolean supportsResultSetConcurrency(int type,
                                                      int concurrency)
                                               throws SQLException

      Implements JDBC 2.0 DatabaseMetaData.supportsResultSetConcurrency. Does the database support the concurrency type in combination with the given result set type? This method always return true.
      Specified by:
      [`supportsResultSetConcurrency`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsResultSetConcurrency_int_int_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `type` - defined in `java.sql.ResultSet`

      `concurrency` - type defined in `java.sql.ResultSet`

      Returns:
      true always

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      See Also:
      [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)

    <!-- -->

    - #### ownUpdatesAreVisible

          public boolean ownUpdatesAreVisible(int type)
                                       throws SQLException

      Implements JDBC 2.0 DatabaseMetaData.ownUpdatesAreVisible. Indicates whether a result set's own updates are visible. Return true for scroll-insensitive and scroll-sensitive resultsets.
      Specified by:
      [`ownUpdatesAreVisible`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#ownUpdatesAreVisible_int_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `type` - result set type, i.e. ResultSet.TYPE_XXX

      Returns:
      `true` if updates are visible for the result set type `false` otherwise

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### ownDeletesAreVisible

          public boolean ownDeletesAreVisible(int type)
                                       throws SQLException

      Implements JDBC 2.0 DatabaseMetaData.ownDeletesAreVisible. Indicates whether a result set's own deletes are visible. Return true for scroll-insensitive and scroll-sensitive resultsets.
      Specified by:
      [`ownDeletesAreVisible`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#ownDeletesAreVisible_int_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `type` - result set type, i.e. ResultSet.TYPE_XXX

      Returns:
      `true` if deletes are visible for the result set type `false` otherwise

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### ownInsertsAreVisible

          public boolean ownInsertsAreVisible(int type)
                                       throws SQLException

      Implements JDBC 2.0 DatabaseMetaData.ownInsertsAreVisible. Indicates whether a result set's own inserts are visible. This method always return false in Oracle JDBC driver.
      Specified by:
      [`ownInsertsAreVisible`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#ownInsertsAreVisible_int_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `type` - result set type, i.e. ResultSet.TYPE_XXX

      Returns:
      `true` if inserts are visible for the result set type `false` otherwise

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### othersUpdatesAreVisible

          public boolean othersUpdatesAreVisible(int type)
                                          throws SQLException

      Implements JDBC 2.0 DatabaseMetaData.. Indicates whether updates made by others are visible. return true for scroll-sensitive result sets; reutrn false otherwise.
      Specified by:
      [`othersUpdatesAreVisible`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#othersUpdatesAreVisible_int_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `type` - result set type, i.e. ResultSet.TYPE_XXX

      Returns:
      `true` if updates made by others are visible for the result set type; `false` otherwise

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### othersDeletesAreVisible

          public boolean othersDeletesAreVisible(int type)
                                          throws SQLException

      Implements JDBC 2.0 DatabaseMetaData.. Indicates whether deletes made by others are visible. This method always return false since Oracle JDBC driver doesn't make others changes visible.
      Specified by:
      [`othersDeletesAreVisible`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#othersDeletesAreVisible_int_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `type` - result set type, i.e. ResultSet.TYPE_XXX

      Returns:
      `true` if deletes made by others are visible for the result set type; `false` otherwise

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### othersInsertsAreVisible

          public boolean othersInsertsAreVisible(int type)
                                          throws SQLException

      Implements JDBC 2.0 DatabaseMetaData.othersInsertsAreVisible. Indicates whether inserts made by others are visible. This method always return false since Oracle JDBC driver doesn't make others changes visible.
      Specified by:
      [`othersInsertsAreVisible`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#othersInsertsAreVisible_int_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `type` - result set type, i.e. ResultSet.TYPE_XXX

      Returns:
      true if updates are visible for the result set type `true` if inserts made by others are visible for the result set type; `false` otherwise

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### updatesAreDetected

          public boolean updatesAreDetected(int type)
                                     throws SQLException

      Implements JDBC 2.0 DatabaseMetaData.updatesAreDetected. Indicates whether or not a visible row update can be detected by calling the method `ResultSet.rowUpdated`. This method always return false since Oracle JDBC driver doesn't detect row changes.
      Specified by:
      [`updatesAreDetected`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#updatesAreDetected_int_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `type` - result set type, i.e. ResultSet.TYPE_XXX

      Returns:
      `true` if changes are detected by the result set type `false` otherwise

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### deletesAreDetected

          public boolean deletesAreDetected(int type)
                                     throws SQLException

      Implements JDBC 2.0 DatabaseMetaData.deletesAreDetected. Indicates whether or not a visible row delete can be detected by calling ResultSet.rowDeleted(). This method always return false since Oracle JDBC driver doesn't detect row changes.
      Specified by:
      [`deletesAreDetected`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#deletesAreDetected_int_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `type` - result set type, i.e. ResultSet.TYPE_XXX

      Returns:
      true if changes are detected by the resultset type

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### insertsAreDetected

          public boolean insertsAreDetected(int type)
                                     throws SQLException

      Implements JDBC 2.0 DatabaseMetaData.insertsAreDetected. Indicates whether or not a visible row insert can be detected by calling ResultSet.rowInserted(). This method always return false since Oracle JDBC driver doesn't detect row changes.
      Specified by:
      [`insertsAreDetected`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#insertsAreDetected_int_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `type` -

      `type` - result set type, i.e. ResultSet.TYPE_XXX

      Returns:
      false always

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### supportsBatchUpdates

          public boolean supportsBatchUpdates()
                                       throws SQLException

      Implements JDBC 2.0 DatabaseMetaData::supportBatchUpdates. Indicates whether the driver supports batch updates.
      Specified by:
      [`supportsBatchUpdates`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsBatchUpdates__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true if the driver supports batch updates false otherwise

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getUDTs

          public ResultSet getUDTs(String catalog,
                                   String schemaPattern,
                                   String typeNamePattern,
                                   int[] types)
                            throws SQLException

      Implements JDBC 2.0 DatabaseMetaData::getUDTs. Gets a description of the STRUCT types defined in a particular schema.
      Only types matching the schema, type name and type criteria are returned. They are ordered by DATA_TYPE, TYPE_SCHEM and TYPE_NAME. The type name parameter may be a fully-qualified name. In this case, the catalog and schemaPattern parameters are ignored.

      Each type description has the following columns:

      1.  **TYPE_CAT** String =\> the type's catalog which is always null
      2.  **TYPE_SCHEM** String =\> type's schema
      3.  **TYPE_NAME** String =\> type name
      4.  **CLASS_NAME** String =\> Java class name
      5.  **DATA_TYPE** String =\> type value defined in java.sql.Types. Only STRUCT is supported.
      6.  **REMARKS** String =\> explanatory comment on the type

      Specified by:
      [`getUDTs`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getUDTs_java_lang_String_java_lang_String_java_lang_String_int_A_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - is ignored since Oracle database doesn't support catalog for structured types

      `schemaPattern` - a schema name pattern; "" retrieves those without a schema

      `typeNamePattern` - a type name pattern; may be a fully-qualified name

      `types` - a list of user-named types to include (Oracle only STRUCT) supports; null returns all types

      Returns:
      ResultSet - each row is a type description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### getConnection

          public Connection getConnection()
                                   throws SQLException

      Implements JDBC 2.0 DatabaseMetaData.getConnection. Retrieves the connection that produced this metadata object.
      Specified by:
      [`getConnection`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getConnection__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the connection that produced this metadata object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsSavepoints

          public boolean supportsSavepoints()
                                     throws SQLException

      JDBC 3.0 Retrieves whether this database supports savepoints.
      Specified by:
      [`supportsSavepoints`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsSavepoints__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      `true` if savepoints are supported `false` otherwise

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### supportsNamedParameters

          public boolean supportsNamedParameters()
                                          throws SQLException

      JDBC 3.0 Retrieves whether this database supports named parameters to callable statements.
      Specified by:
      [`supportsNamedParameters`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsNamedParameters__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      `true` if named parameters are supported `false` otherwise

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### supportsMultipleOpenResults

          public boolean supportsMultipleOpenResults()
                                              throws SQLException

      JDBC 3.0 Retrieves whether it is possible to have multiple `ResultSet` objects returned from a `CallableStatement` object simultaneously.
      Specified by:
      [`supportsMultipleOpenResults`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsMultipleOpenResults__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      `true` if a `CallableStatement` object can return multiple `ResultSet` objects simultaneously; `false` otherwise

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a datanase access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### supportsGetGeneratedKeys

          public boolean supportsGetGeneratedKeys()
                                           throws SQLException

      JDBC 3.0 Retrieves whether auto-generated keys can be retrieved after a statement has been executed.
      Specified by:
      [`supportsGetGeneratedKeys`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsGetGeneratedKeys__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      `true` if auto-generated keys can be retrieved after a statement has executed; `false` otherwise

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### getSuperTypes

          public ResultSet getSuperTypes(String catalog,
                                         String schemaPattern,
                                         String typeNamePattern)
                                  throws SQLException

      JDBC 3.0 Retrieves a description of the user-defined type (UDT) hierarchies defined in a particular schema in this database. Only the immediate super type/sub type relationship is modeled.
      Only supertype information for UDTs matching the catalog, schema, and type name is returned. The type name parameter may be a fully-qualified name. When the UDT name supplied is a fully-qualified name, the catalog and schemaPattern parameters are ignored.

      If a UDT does not have a direct super type, it is not listed here. A row of the `ResultSet` object returned by this method describes the designated UDT and a direct supertype. A row has the following columns:

      1.  **TYPE_CAT** String =\> the UDT's catalog (may be `null`)
      2.  **TYPE_SCHEM** String =\> UDT's schema (may be `null`)
      3.  **TYPE_NAME** String =\> type name of the UDT
      4.  **SUPERTYPE_CAT** String =\> the direct super type's catalog (may be `null`)
      5.  **SUPERTYPE_SCHEM** String =\> the direct super type's schema (may be `null`)
      6.  **SUPERTYPE_NAME** String =\> the direct super type's name

      **Note:** If the driver does not support type hierarchies, an empty result set is returned.

      Specified by:
      [`getSuperTypes`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getSuperTypes_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; "" retrieves those without a catalog; `null` means drop catalog name from the selection criteria

      `schemaPattern` - a schema name pattern; "" retrieves those without a schema

      `typeNamePattern` - a UDT name pattern; may be a fully-qualified name

      Returns:
      a `ResultSet` object in which a row gives information about the designated UDT

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### getSuperTables

          public ResultSet getSuperTables(String catalog,
                                          String schemaPattern,
                                          String tableNamePattern)
                                   throws SQLException

      JDBC 3.0 Retrieves a description of the table hierarchies defined in a particular schema in this database.
      Only supertable information for tables matching the catalog, schema and table name are returned. The table name parameter may be a fully- qualified name, in which case, the catalog and schemaPattern parameters are ignored. If a table does not have a super table, it is not listed here. Supertables have to be defined in the same catalog and schema as the sub tables. Therefore, the type description does not need to include this information for the supertable.

      Each type description has the following columns:

      1.  **TABLE_CAT** String =\> the type's catalog (may be `null`)
      2.  **TABLE_SCHEM** String =\> type's schema (may be `null`)
      3.  **TABLE_NAME** String =\> type name
      4.  **SUPERTABLE_NAME** String =\> the direct super type's name

      **Note:** If the driver does not support type hierarchies, an empty result set is returned.

      Specified by:
      [`getSuperTables`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getSuperTables_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; "" retrieves those without a catalog; `null` means drop catalog name from the selection criteria

      `schemaPattern` - a schema name pattern; "" retrieves those without a schema

      `tableNamePattern` - a table name pattern; may be a fully-qualified name

      Returns:
      a `ResultSet` object in which each row is a type description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### getAttributes

          public ResultSet getAttributes(String catalog,
                                         String schemaPattern,
                                         String typeNamePattern,
                                         String attributeNamePattern)
                                  throws SQLException

      JDBC 3.0 Retrieves a description of the given attribute of the given type for a user-defined type (UDT) that is available in the given schema and catalog.
      Descriptions are returned only for attributes of UDTs matching the catalog, schema, type, and attribute name criteria. They are ordered by TYPE_SCHEM, TYPE_NAME and ORDINAL_POSITION. This description does not contain inherited attributes.

      The `ResultSet` object that is returned has the following columns:

      1.  **TYPE_CAT** String =\> type catalog (may be `null`)
      2.  **TYPE_SCHEM** String =\> type schema (may be `null`)
      3.  **TYPE_NAME** String =\> type name
      4.  **ATTR_NAME** String =\> attribute name
      5.  **DATA_TYPE** short =\> attribute type SQL type from java.sql.Types
      6.  **ATTR_TYPE_NAME** String =\> Data source dependent type name. For a UDT, the type name is fully qualified. For a REF, the type name is fully qualified and represents the target type of the reference type.
      7.  **ATTR_SIZE** int =\> column size. For char or date types this is the maximum number of characters; for numeric or decimal types this is precision.
      8.  **DECIMAL_DIGITS** int =\> the number of fractional digits
      9.  **NUM_PREC_RADIX** int =\> Radix (typically either 10 or 2)
      10. **NULLABLE** int =\> whether NULL is allowed
          - attributeNoNulls - might not allow NULL values
          - attributeNullable - definitely allows NULL values
          - attributeNullableUnknown - nullability unknown
      11. **REMARKS** String =\> comment describing column (may be `null`)
      12. **ATTR_DEF** String =\> default value (may be `null`)
      13. **SQL_DATA_TYPE** int =\> unused
      14. **SQL_DATETIME_SUB** int =\> unused
      15. **CHAR_OCTET_LENGTH** int =\> for char types the maximum number of bytes in the column
      16. **ORDINAL_POSITION** int =\> index of column in table (starting at 1)
      17. **IS_NULLABLE** String =\> "NO" means column definitely does not allow NULL values; "YES" means the column might allow NULL values. An empty string means unknown.
      18. **SCOPE_CATALOG** String =\> catalog of table that is the scope of a reference attribute (`null` if DATA_TYPE isn't REF)
      19. **SCOPE_SCHEMA** String =\> schema of table that is the scope of a reference attribute (`null` if DATA_TYPE isn't REF)
      20. **SCOPE_TABLE** String =\> table name that is the scope of a reference attribute (`null` if the DATA_TYPE isn't REF)
      21. **SOURCE_DATA_TYPE** short =\> source type of a distinct type or user-generated Ref type,SQL type from java.sql.Types (`null` if DATA_TYPE isn't DISTINCT or user-generated REF)

      Specified by:
      [`getAttributes`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getAttributes_java_lang_String_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - a catalog name; must match the catalog name as it is stored in the database; "" retrieves those without a catalog; `null` means that the catalog name should not be used to narrow the search

      `schemaPattern` - a schema name pattern; must match the schema name as it is stored in the database; "" retrieves those without a schema; `null` means that the schema name should not be used to narrow the search

      `typeNamePattern` - a type name pattern; must match the type name as it is stored in the database

      `attributeNamePattern` - an attribute name pattern; must match the attribute name as it is declared in the database

      Returns:
      a `ResultSet` object in which each row is an attribute description

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### supportsResultSetHoldability

          public boolean supportsResultSetHoldability(int holdability)
                                               throws SQLException

      JDBC 3.0 Retrieves whether this database supports the given result set holdability.
      Specified by:
      [`supportsResultSetHoldability`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsResultSetHoldability_int_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `holdability` - one of the following constants: `ResultSet.HOLD_CURSORS_OVER_COMMIT` or `ResultSet.CLOSE_CURSORS_AT_COMMIT` or `OracleResultSet.HOLD_CURSORS_OVER_COMMIT for jdk1.2 and jdk1.3` or `OracleResultSet.CLOSE_CURSORS_AT_COMMIT for jdk1.2 and jdk1.3`

      Returns:
      `true` if so `false` otherwise

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)

    <!-- -->

    - #### getResultSetHoldability

          public int getResultSetHoldability()
                                      throws SQLException

      JDBC 3.0 Retrieves the default holdability of this `ResultSet` object.
      Specified by:
      [`getResultSetHoldability`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getResultSetHoldability__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the default holdability either `ResultSet.HOLD_CURSORS_OVER_COMMIT` or `ResultSet.CLOSE_CURSORS_AT_COMMIT` or `OracleResultSet.HOLD_CURSORS_OVER_COMMIT` for jdk1.2 and jdk1.3 or `OracleResultSet.CLOSE_CURSORS_AT_COMMIT` for jdk1.2 and jdk1.3

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### getDatabaseMajorVersion

          public int getDatabaseMajorVersion()
                                      throws SQLException

      JDBC 3.0 Retrieves the major version number of the underlying database.
      Specified by:
      [`getDatabaseMajorVersion`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getDatabaseMajorVersion__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the underlying database's major version

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### getDatabaseMinorVersion

          public int getDatabaseMinorVersion()
                                      throws SQLException

      JDBC 3.0 Retrieves the minor version number of the underlying database.
      Specified by:
      [`getDatabaseMinorVersion`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getDatabaseMinorVersion__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      underlying database's minor version

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### getJDBCMajorVersion

          public int getJDBCMajorVersion()
                                  throws SQLException

      JDBC 3.0 Retrieves the major JDBC version number for this driver.
      Specified by:
      [`getJDBCMajorVersion`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getJDBCMajorVersion__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      JDBC version major number

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### getJDBCMinorVersion

          public int getJDBCMinorVersion()
                                  throws SQLException

      JDBC 3.0 Retrieves the minor JDBC version number for this driver.
      Specified by:
      [`getJDBCMinorVersion`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getJDBCMinorVersion__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      JDBC version minor number

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### getSQLStateType

          public int getSQLStateType()
                              throws SQLException

      JDBC 3.0 Indicates whether the SQLSTATEs returned by `SQLException.getSQLState` is X/Open (now known as Open Group) SQL CLI or SQL99.
      Specified by:
      [`getSQLStateType`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getSQLStateType__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      the type of SQLSTATEs, one of: sqlStateXOpen or sqlStateSQL99

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### locatorsUpdateCopy

          public boolean locatorsUpdateCopy()
                                     throws SQLException

      JDBC 3.0
      Specified by:
      [`locatorsUpdateCopy`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#locatorsUpdateCopy__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### supportsStatementPooling

          public boolean supportsStatementPooling()
                                           throws SQLException

      JDBC 3.0
      Specified by:
      [`supportsStatementPooling`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsStatementPooling__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDriverNameInfo

          public static String getDriverNameInfo()
                                          throws SQLException

      What's the name of this JDBC driver?
      Returns:
      JDBC driver name

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDriverVersionInfo

          public static String getDriverVersionInfo()
                                             throws SQLException

      Deprecated. -- use standard getDriverVersion()
      What's the version of this JDBC driver?
      Returns:
      JDBC driver version

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDriverMajorVersionInfo

          public static int getDriverMajorVersionInfo()

      Deprecated. -- use standard getDriverMajorVersion()
      What's this JDBC driver's major version number?
      Returns:
      JDBC driver major version

    <!-- -->

    - #### getDriverMinorVersionInfo

          public static int getDriverMinorVersionInfo()

      Deprecated. -- use JDBC standard method getDriverMinorVersion
      What's this JDBC driver's minor version number?
      Returns:
      JDBC driver minor version number

    <!-- -->

    - #### getLobPrecision

          public static String getLobPrecision()
                                        throws SQLException

      Deprecated. 
      This is an internal method that should not be used by customers.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getLobMaxLength

          public long getLobMaxLength()
                               throws SQLException

      The max size of a lob on the server for this connection. Note that the actual size available for a particular lob will depend on the specific storage allocation.
      Specified by:
      [`getLobMaxLength`](AdditionalDatabaseMetaData.md) in interface [`AdditionalDatabaseMetaData`](AdditionalDatabaseMetaData.md)

      Returns:
      Max size of lob.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getRowIdLifetime

          public RowIdLifetime getRowIdLifetime()
                                         throws SQLException

      Oracle rowids are valid across all sessions.
      Specified by:
      [`getRowIdLifetime`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getRowIdLifetime__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.0

    <!-- -->

    - #### getSchemas

          public ResultSet getSchemas(String catalog,
                                      String schemaPattern)
                               throws SQLException

      Return the schemas that match the given pattern. Oracle does not support catalogs so that parameter is ignored. If the pattern is null that means don't filter using a pattern. Since the catalog is ignored that is the same as the getSchemas() method so call it.
      The schema columns are:

      1.  **TABLE_SCHEM** String =\> schema name
      2.  **TABLE_CATALOG** String =\> catalog name always `null`.

      Specified by:
      [`getSchemas`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getSchemas_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - ignored

      `schemaPattern` - pattern to match against the schema names

      Returns:
      a result set of schema names

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11.0

    <!-- -->

    - #### supportsStoredFunctionsUsingCallSyntax

          public boolean supportsStoredFunctionsUsingCallSyntax()
                                                         throws SQLException

      Oracle supports using the JDBC escape syntax to call PLSQL functions.
      Specified by:
      [`supportsStoredFunctionsUsingCallSyntax`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#supportsStoredFunctionsUsingCallSyntax__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      true

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.0

    <!-- -->

    - #### autoCommitFailureClosesAllResultSets

          public boolean autoCommitFailureClosesAllResultSets()
                                                       throws SQLException

      Oracle does not close ResultSets when autocommit fails.
      Specified by:
      [`autoCommitFailureClosesAllResultSets`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#autoCommitFailureClosesAllResultSets__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Returns:
      false

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.0

    <!-- -->

    - #### getClientInfoProperties

          public ResultSet getClientInfoProperties()
                                            throws SQLException

      Specified by:
      [`getClientInfoProperties`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getClientInfoProperties__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getFunctions

          public ResultSet getFunctions(String catalog,
                                        String schemaPattern,
                                        String functionNamePattern)
                                 throws SQLException

      Return a result set that describes the matching functions.
      Specified by:
      [`getFunctions`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getFunctions_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Parameters:
      `catalog` - used for the package name

      `schemaPattern` - the schema pattern to match

      `functionNamePattern` - the pattern to match against the function name

      Returns:
      a ResultSet that describes the matching functions

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.0

    <!-- -->

    - #### isWrapperFor

          public boolean isWrapperFor(Class<?> iface)
                               throws SQLException

      Since this class is not a wrapper, just check to see if this implements the requested interface.
      Specified by:
      [`isWrapperFor`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#isWrapperFor_java_lang_Class_) in interface [`Wrapper`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      Parameters:
      `iface` - requested interface

      Returns:
      true iff this implements the requested interface

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the arg is not an interface

      Since:
      JDBC 4.0

    <!-- -->

    - #### unwrap

          public <T> T unwrap(Class<T> iface)
                       throws SQLException

      Since this class is not a wrapper, just check to see if this implements the requested interface. If it does return this.
      Specified by:
      [`unwrap`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#unwrap_java_lang_Class_) in interface [`Wrapper`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      Parameters:
      `iface` - requested interface

      Returns:
      this iff this implements the requested interface

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if this does not implement the arg or the arg is not an interface

      Since:
      JDBC 4.0

    <!-- -->

    - #### hasSqlWildcard

          protected boolean hasSqlWildcard(String s)

    <!-- -->

    - #### stripSqlEscapes

          protected String stripSqlEscapes(String s)

    <!-- -->

    - #### getOracleTypeMetaData

          public OracleTypeMetaData getOracleTypeMetaData(String sqlTypeName)
                                                   throws SQLException

      Description copied from interface: [`AdditionalDatabaseMetaData`](AdditionalDatabaseMetaData.md)
      Return the type metadata for a named type. Use this instead of the various Descriptor classes and methods. Use of the Descriptor classes and methods such as oracle.sql.TypeDescriptor, is not recommended and will cause ClassCastException if used with some new Oracle JDBC features.
      Specified by:
      [`getOracleTypeMetaData`](AdditionalDatabaseMetaData.md) in interface [`AdditionalDatabaseMetaData`](AdditionalDatabaseMetaData.md)

      Parameters:
      `sqlTypeName` - the name of the type

      Returns:
      the metadata for the type

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the type does not exist or some other error occurs

    <!-- -->

    - #### datatypeQuery

          protected String datatypeQuery(OracleDatabaseMetaData.DataTypeSource src)

    <!-- -->

    - #### datatypeQuery

          protected String datatypeQuery(OracleDatabaseMetaData.DataTypeSource src,
                                         String table)

    <!-- -->

    - #### getPseudoColumns

          public ResultSet getPseudoColumns(String catalog,
                                            String schemaPattern,
                                            String tableNamePattern,
                                            String columnNamePattern)
                                     throws SQLException

      Specified by:
      [`getPseudoColumns`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#getPseudoColumns_java_lang_String_java_lang_String_java_lang_String_java_lang_String_) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### generatedKeyAlwaysReturned

          public boolean generatedKeyAlwaysReturned()
                                             throws SQLException

      Specified by:
      [`generatedKeyAlwaysReturned`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true#generatedKeyAlwaysReturned__) in interface [`DatabaseMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getAuditBanner

          public String getAuditBanner()
                                throws SQLException

      Returns the audit banner on this connection.
      Specified by:
      [`getAuditBanner`](AdditionalDatabaseMetaData.md) in interface [`AdditionalDatabaseMetaData`](AdditionalDatabaseMetaData.md)

      Returns:
      String containing the audit banner or a null String if there isn't one available on this connection.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is any issue while retrieving the banner

    <!-- -->

    - #### getAccessBanner

          public String getAccessBanner()
                                 throws SQLException

      Returns the access banner on this connection.
      Specified by:
      [`getAccessBanner`](AdditionalDatabaseMetaData.md) in interface [`AdditionalDatabaseMetaData`](AdditionalDatabaseMetaData.md)

      Returns:
      String containing the access banner or a null String if there isn't one available on this connection.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is any issue while retrieving the banner

    <!-- -->

    - #### isServerBigSCN

          public boolean isServerBigSCN()
                                 throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isCompatible122OrGreater

          public boolean isCompatible122OrGreater()
                                           throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setACProxy

          public void setACProxy(Object w)

      Specified by:
      `setACProxy` in interface `oracle.jdbc.internal.ACProxyable`

    <!-- -->

    - #### getACProxy

          public Object getACProxy()

      Specified by:
      `getACProxy` in interface `oracle.jdbc.internal.ACProxyable`

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleDatabaseMetaData.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleDatabaseException.md)
- [Next Class](OracleDatabaseMetaData.DataTypeSource.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2008, 2022, Oracle and/or its affiliates.
