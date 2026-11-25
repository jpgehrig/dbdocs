Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleClob.md)
- [Next Class](OracleConnection.CommitOption.md)

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

## Interface OracleConnection

- All Superinterfaces:
  [AutoCloseable](http://download.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true), [Connection](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

  <!-- -->

  All Known Implementing Classes:
  [OracleConnectionWrapper](OracleConnectionWrapper.md)

  ------------------------------------------------------------------------



      public interface OracleConnection
      extends Connection

  This interface defines the Oracle extensions to the standard JDBC interface `java.sql.Connection`. You can use `java.sql.Connection` in your application where you do not make use of the Oracle extensions. However, when your application uses the Oracle extensions to `java.sql.Connection` you must use `oracle.jdbc.OracleConnection`.
  `OracleConnection` extends standard JDBC connection functionality to create and return Oracle statement objects, set flags and options for Oracle performance extensions, and support type maps for Oracle objects.

  Basic example : Once you connect to the database and, in the process, create your `Connection` object (see [OracleDriver](OracleDriver.md)), the next step is to create a `Statement` object. The `createStatement` method of your JDBC `Connection` object returns an object of the JDBC Statement type.
  Here is an example of how to create the `Statement` object (`conn` being your connection object):

  `Statement stmt = conn.createStatement();`

  Note that there is nothing Oracle-specific about this statement; it follows standard JDBC syntax.

  Since:
  8.1.7

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Interface and Description                                                                                                                                                                                                                              |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`OracleConnection.CommitOption`](OracleConnection.CommitOption.md)                                                                                                                                                                                    |
    | `static class `   | [`OracleConnection.ConnectionValidation`](OracleConnection.ConnectionValidation.md)<br>Specifiers for how much effort to put into validating a [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true). |
    | `static class `   | [`OracleConnection.DatabaseShutdownMode`](OracleConnection.DatabaseShutdownMode.md)                                                                                                                                                                    |
    | `static class `   | [`OracleConnection.DatabaseStartupMode`](OracleConnection.DatabaseStartupMode.md)                                                                                                                                                                      |
    | `static class `   | [`OracleConnection.DRCPState`](OracleConnection.DRCPState.md)                                                                                                                                                                                          |

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type                                                                                        | Field and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    |----------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`                                                                                             | `ABANDONED_CONNECTION_CALLBACK`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static byte`                                                                                            | `ACCESSMODE_BOTH`<br>Bitmask which can be applied to the `CONNECTION_PROPERTY_{name}_ACCESSMODE` constants defined in this interface.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static byte`                                                                                            | `ACCESSMODE_FILEPROP`<br>Bitmask which can be applied to the `CONNECTION_PROPERTY_{name}_ACCESSMODE` constants defined in this interface.                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static byte`                                                                                            | `ACCESSMODE_JAVAPROP`<br>Bitmask which can be applied to the `CONNECTION_PROPERTY_{name}_ACCESSMODE` constants defined in this interface.                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static byte`                                                                                            | `ACCESSMODE_SYSTEMPROP`<br>Bitmask which can be applied to the `CONNECTION_PROPERTY_{name}_ACCESSMODE` constants defined in this interface.                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static int`                                                                                             | `ALL_CONNECTION_CALLBACKS`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static int`                                                                                             | `CACHE_SIZE_NOT_SET`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CLIENT_INFO_KEY_SEPARATOR`<br>Separate the namespace from the key the name of a client info.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ACCESS_TOKEN`<br>This property configures an access token that Oracle JDBC uses for authentication with Oracle Database.                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_ACCESS_TOKEN_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ACCESS_TOKEN_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ACCUMULATE_BATCH_RESULT`<br>When using Oracle style batching, JDBC determines when to flush a batch to the database.                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_ACCUMULATE_BATCH_RESULT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ACCUMULATE_BATCH_RESULT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ALLOWED_LOGON_VERSION`<br>Minimum authentication protocol required by the client.                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_ALLOWED_LOGON_VERSION_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ALLOWED_LOGON_VERSION_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_AUTO_COMMIT_SPEC_COMPLIANT`<br>Alters the auto-commit behavior of the driver.                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_AUTO_COMMIT_SPEC_COMPLIANT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_AUTO_COMMIT_SPEC_COMPLIANT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_AUTOCOMMIT`<br>Use this connection property to change the default value of autoCommit.                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_AUTOCOMMIT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_AUTOCOMMIT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_BACKWARD_COMPATIBLE_UPDATEABLE_RESULTSET`<br>If set to true, use the old, pre 12.1.0.2.0, updateable ResultSet behavior.                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_BACKWARD_COMPATIBLE_UPDATEABLE_RESULTSET_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_BACKWARD_COMPATIBLE_UPDATEABLE_RESULTSET_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_COMMIT_OPTION`<br>This connection property lets you define a default commit option that will be used when calling `connection.commit();`.                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_COMMIT_OPTION_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_COMMIT_OPTION_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_CONFIG_FILE`<br>This property provides the location of one or more properties files.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_CONFIG_FILE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_CONFIG_FILE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_CONNECTION_CLASS`<br>Specify the connection class name for Database Resident Connection Pool (DRCP).                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_CONNECTION_CLASS_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_CONNECTION_CLASS_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_CONNECTION_PURITY`<br>Specify the connection purity for a Database Resident Connection Pool (DRCP) connection.                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_CONNECTION_PURITY_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_CONNECTION_PURITY_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_CONVERT_NCHAR_LITERALS`<br>Convert NCHAR literals to Unicode literals when equal "true".                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_CONVERT_NCHAR_LITERALS_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_CONVERT_NCHAR_LITERALS_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_CREATE_DESCRIPTOR_USE_CURRENT_SCHEMA_FOR_SCHEMA_NAME`<br>The user has to provide fully qualified ADT name (\[username\].\[adt name\]) for all ADT operations.                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_CREATE_DESCRIPTOR_USE_CURRENT_SCHEMA_FOR_SCHEMA_NAME_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_CREATE_DESCRIPTOR_USE_CURRENT_SCHEMA_FOR_SCHEMA_NAME_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DATABASE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_DATABASE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DATABASE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DEFAULT_CONNECTION_VALIDATION`<br>This connection property is used to specify how much effort to put into validating a [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true).<br>This property controls what isValid() does.<br>The possible values for this property are - "NONE", "LOCAL", "SOCKET", "NETWORK", "SERVER" and "COMPLETE".<br>The values are case-sensitive, setting any other value throws exception.<br>The default value of this property is "NETWORK".<br>                  |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_DEFAULT_CONNECTION_VALIDATION_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DEFAULT_CONNECTION_VALIDATION_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DEFAULT_EXECUTE_BATCH`<br>Deprecated. <br>Oracle-Style batching is desupported. Standard JDBC batch execution is recommended instead.                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_DEFAULT_EXECUTE_BATCH_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DEFAULT_EXECUTE_BATCH_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DEFAULT_LOB_PREFETCH_SIZE`<br>The value of this property is used as the default LOB prefetch size for this connection.                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_DEFAULT_LOB_PREFETCH_SIZE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DEFAULT_LOB_PREFETCH_SIZE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DEFAULT_ROW_PREFETCH`<br>The value of this property is used as the default number of rows to prefetch.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_DEFAULT_ROW_PREFETCH_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DEFAULT_ROW_PREFETCH_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DEFAULT_USE_NIO`<br>In case of Jdbc-OCI drivers the data is copied from C layer to Java using Jni array copy api.                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_DEFAULT_USE_NIO_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DEFAULT_USE_NIO_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DEFAULTNCHAR`<br>If the value of this property is "true", the default mode for all character data columns will be NCHAR.                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_DEFAULTNCHAR_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DEFAULTNCHAR_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DISABLE_DEFINECOLUMNTYPE`<br>Disable the method OracleStatement.defineColumnType when equal "true".                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_DISABLE_DEFINECOLUMNTYPE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DISABLE_DEFINECOLUMNTYPE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DOWN_HOSTS_TIMEOUT`<br>To specify the amount of time in seconds that information about the `down` state of server hosts is kept in driver's cache.                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_DOWN_HOSTS_TIMEOUT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DOWN_HOSTS_TIMEOUT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DRCP_PLSQL_CALLBACK`<br>This is PL/SQL `"fix-up"` callback name which is provided by the application, and it is used to transform a session checked out from the pool to the desired state requested by the application.<br>`"fix-up"` callback can provide performance improvements to applications by running the `"session state fix-up"` logic on the server, thereby eliminating application round-trips to the database to run the `"fix-up"` logic.<br>This is an optional configuration.<br>This property is valid only for thin driver. |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_DRCP_PLSQL_CALLBACK_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DRCP_PLSQL_CALLBACK_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DRCP_TAG_NAME`<br>This is the tag name that for Database Resident Connection Pool (DRCP).                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_DRCP_TAG_NAME_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DRCP_TAG_NAME_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DRIVER_NAME_ATTRIBUTE`<br>The value passed to the server for the OCI_ATTR_DRIVER_NAME.                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_DRIVER_NAME_ATTRIBUTE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_DRIVER_NAME_ATTRIBUTE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_EDITION_NAME`<br>This connection property can be used to specify a name for the "session edition".                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_EDITION_NAME_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_EDITION_NAME_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_AC_SUPPORT`<br>Specifies whether driver support for Application Continuity (AC) is enabled.                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_ENABLE_AC_SUPPORT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_AC_SUPPORT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_DATA_IN_LOCATOR`<br>The value of this property is used to control the use of the Data in Locator feature of the server.                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_ENABLE_DATA_IN_LOCATOR_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_DATA_IN_LOCATOR_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_IMPLICIT_REQUESTS`<br>Specifies whether to enable implicit request boundary support for Application Continuity (AC).                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_ENABLE_IMPLICIT_REQUESTS_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_IMPLICIT_REQUESTS_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_QUERY_RESULT_CACHE`<br>This property is introduced in 18c.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_ENABLE_QUERY_RESULT_CACHE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_QUERY_RESULT_CACHE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_READ_DATA_IN_LOCATOR`<br>The value of this property is used to control the use of the Data in Locator feature by the client.                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_ENABLE_READ_DATA_IN_LOCATOR_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_READ_DATA_IN_LOCATOR_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_RESULTSET_CACHE`<br>This property is ignored in 18c.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_ENABLE_RESULTSET_CACHE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_RESULTSET_CACHE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_TEMP_LOB_REF_COUNT`<br>By default the JDBC thin driver counts the temp LOB references and only closes them on the server when this count is down to zero.                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_ENABLE_TEMP_LOB_REF_COUNT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_TEMP_LOB_REF_COUNT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_TG_SUPPORT`<br>Specifies whether driver support for Transaction Guard (TG) is enabled.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_ENABLE_TG_SUPPORT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_ENABLE_TG_SUPPORT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_FAN_ENABLED`<br>Specifies whether driver High Availability (HA) or FAN (Fast Application Notification) is enabled.                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_FAN_ENABLED_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_FAN_ENABLED_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_FIXED_STRING`<br>If the value of this property is "true", JDBC will use FIXED CHAR semantic when setObject is called with a String argument.                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_FIXED_STRING_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_FIXED_STRING_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_IMPLICIT_STATEMENT_CACHE_SIZE`<br>The maximum number of statements that will be stored in this connection's statement cache.                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_IMPLICIT_STATEMENT_CACHE_SIZE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_IMPLICIT_STATEMENT_CACHE_SIZE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_IN_BAND_NOTIFICATION`<br>Specifies whether driver in-band notification support is enabled.                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_IN_BAND_NOTIFICATION_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_IN_BAND_NOTIFICATION_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_INCLUDE_SYNONYMS`<br>If the value of this property is "true", JDBC will include synonyms when getting information about a column.                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_INCLUDE_SYNONYMS_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_INCLUDE_SYNONYMS_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_INTERNAL_LOGON`<br>The value of this property is used as the user name when performing an internal logon.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_INTERNAL_LOGON_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_INTERNAL_LOGON_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_J2EE13_COMPLIANT`<br>Deprecated. <br>This property could be removed in the future and the default will be `true`. So if this property is used as workaround to turn off compliant behavior, consider changing the application.                                                                                                                                                                                                                                                                                                                   |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_J2EE13_COMPLIANT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_J2EE13_COMPLIANT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_JDBC_STANDARD_BEHAVIOR`<br>Ensures the driver is in strict compliance with the JDBC specification.                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_JDBC_STANDARD_BEHAVIOR_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_JDBC_STANDARD_BEHAVIOR_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_LOB_STREAM_POS_STANDARD_COMPLIANT`<br>Previous releases allowed the value of 0L to be set for the position parameter of Blob.setBinaryStream and Clob.setAsciiStream and setCharacterStream which is not correct in the specification.                                                                                                                                                                                                                                                                                                           |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_LOB_STREAM_POS_STANDARD_COMPLIANT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_LOB_STREAM_POS_STANDARD_COMPLIANT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_MAP_DATE_TO_TIMESTAMP`<br>This connection property lets you define how the driver will map SQL DATE values in the database to Java types.                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_MAP_DATE_TO_TIMESTAMP_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_MAP_DATE_TO_TIMESTAMP_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_MAX_CACHED_BUFFER_SIZE`<br>The log base 2 of the size of the largest internal char or byte data buffer that the driver should cache.                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_MAX_CACHED_BUFFER_SIZE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_MAX_CACHED_BUFFER_SIZE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_NET_KEEPALIVE`<br>Sets keepAlive on the Connection Socket.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_NET_KEEPALIVE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_NET_KEEPALIVE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_NETWORK_COMPRESSION`<br>Enables compression of the protocol data sent over network.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_NETWORK_COMPRESSION_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_NETWORK_COMPRESSION_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_NETWORK_COMPRESSION_LEVELS`<br>The value is a comma separated list of supported levels in the user preference order surrounded by brackets.                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_NETWORK_COMPRESSION_LEVELS_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_NETWORK_COMPRESSION_LEVELS_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_NETWORK_COMPRESSION_THRESHOLD`<br>Minimum size of data in packet required to perform compression.                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_NETWORK_COMPRESSION_THRESHOLD_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_NETWORK_COMPRESSION_THRESHOLD_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_NEW_PASSWORD`<br>This property enables users to set a new password during connection creation if user's password got expired.                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_NEW_PASSWORD_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_NEW_PASSWORD_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_COMPARTMENT`<br>When `CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION` is set to "OCI_TOKEN", this property specifies the Oracle Cloud ID (OCID) of the compartment for the database identified by `CONNECTION_PROPERTY_OCI_DATABASE`.                                                                                                                                                                                                                                                                                                           |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_OCI_COMPARTMENT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_COMPARTMENT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_DATABASE`<br>When `CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION` is set to "OCI_TOKEN", this property specifies the Oracle Cloud ID (OCID) of the database that JDBC requests access to.                                                                                                                                                                                                                                                                                                                                                      |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_OCI_DATABASE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_DATABASE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_DRIVER_CHARSET`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_OCI_DRIVER_CHARSET_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_DRIVER_CHARSET_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_ENV_HANDLE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_OCI_ENV_HANDLE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_ENV_HANDLE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_ERR_HANDLE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_OCI_ERR_HANDLE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_ERR_HANDLE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_IAM_URL`<br>When `CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION` is set to "OCI_TOKEN", this property must specify the full path of the Identity and Access Management (IAM) endpoint that Oracle JDBC authenticates with, as in:                                                                                                                                                                                                                                                                                                              |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_OCI_IAM_URL_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_IAM_URL_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_SVC_CTX_HANDLE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_OCI_SVC_CTX_HANDLE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_SVC_CTX_HANDLE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_TENANCY`<br>When `CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION` is set to "OCI_TOKEN", this property must specify the Oracle Cloud ID (OCID) of the cloud tenant for the user that Oracle JDBC authenticates as.                                                                                                                                                                                                                                                                                                                              |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_OCI_TENANCY_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_OCI_TENANCY_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_PASSWORD`<br>The value of this property is used as the password when connecting to the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_PASSWORD_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION`<br>Configures how Oracle JDBC performs authentication with a user name and password.                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_PASSWORD_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_PRELIM_AUTH`<br>If this property is set to "true", JDBC drivers connect in PRELIM_AUTH mode, which is the only mode that is permitted when the database is down.                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_PRELIM_AUTH_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_PRELIM_AUTH_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_PROCESS_ESCAPES`<br>If the value of this property is "false" then the default setting for Statement.setEscapeProccessing is false.                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_PROCESS_ESCAPES_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_PROCESS_ESCAPES_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_PROTOCOL`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_PROTOCOL_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_PROTOCOL_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_PROXY_CLIENT_NAME`<br>The value of this property is used to specify the name of the proxy client during proxy authentication.                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_PROXY_CLIENT_NAME_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_PROXY_CLIENT_NAME_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_REPORT_REMARKS`<br>If the value of this property is "true", OracleDatabaseMetaData will include remarks in the meta data.                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_REPORT_REMARKS_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_REPORT_REMARKS_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_REQUEST_SIZE_LIMIT`<br>Specifies the maximum request size, in terms of number of JDBC calls, beyond which AC replay will be disabled.                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_REQUEST_SIZE_LIMIT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_REQUEST_SIZE_LIMIT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_RESOURCE_MANAGER_ID`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_RESOURCE_MANAGER_ID_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_RESOURCE_MANAGER_ID_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_RESTRICT_GETTABLES`<br>If the value of this property is "true", JDBC will return a more refined value for DatabaseMeta.getTables.                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_RESTRICT_GETTABLES_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_RESTRICT_GETTABLES_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_RETAIN_V9_BIND_BEHAVIOR`<br>This is applicable only for the thin driver.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_RETAIN_V9_BIND_BEHAVIOR_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_RETAIN_V9_BIND_BEHAVIOR_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_SERVER`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_SERVER_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_SERVER_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_SET_FLOAT_AND_DOUBLE_USE_BINARY`<br>If the value of this property is "true", the JDBC PreparedStatement setFloat and setDouble API's convert float and double values to the internal binary format for BINARY_FLOAT or BINARY_DOUBLE before sending to the database.                                                                                                                                                                                                                                                                             |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_SET_FLOAT_AND_DOUBLE_USE_BINARY_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_SET_FLOAT_AND_DOUBLE_USE_BINARY_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_SET_NEW_PASSWORD`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_SET_NEW_PASSWORD_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_SET_NEW_PASSWORD_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_SQL_ERROR_TRANSLATION_FILE`<br>Path to an xml file which provides the Error code translations for those errors which occur if a connection can not be established to the server.                                                                                                                                                                                                                                                                                                                                                                 |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_SQL_ERROR_TRANSLATION_FILE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_SQL_ERROR_TRANSLATION_FILE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_SQL_TRANSLATION_PROFILE`<br>The string identifier for the translation profile or the translator to be used.                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_SQL_TRANSLATION_PROFILE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_SQL_TRANSLATION_PROFILE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_STREAM_CHUNK_SIZE`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_STREAM_CHUNK_SIZE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_STREAM_CHUNK_SIZE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_STRICT_ASCII_CONVERSION`<br>The Oracle JDBC has been doing quick ASCII conversion (use only the low bytes) in different areas for the sake of performance.                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_STRICT_ASCII_CONVERSION_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_STRICT_ASCII_CONVERSION_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_FORCE_DNS_LOAD_BALANCING`<br>When a hostname resolves to multiple addresses, the JDBC thin driver retrieves an array of addresses by calling "InetAddress.getAllByName()" and attempts to connect to first address in the array.                                                                                                                                                                                                                                                                                                            |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_FORCE_DNS_LOAD_BALANCING_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_FORCE_DNS_LOAD_BALANCING_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTOREPASSWORD`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTOREPASSWORD_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTOREPASSWORD_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORETYPE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORETYPE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORETYPE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTOREPASSWORD`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTOREPASSWORD_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTOREPASSWORD_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORETYPE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORETYPE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORETYPE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JNDI_LDAP_CONNECT_TIMEOUT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_JNDI_LDAP_CONNECT_TIMEOUT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JNDI_LDAP_CONNECT_TIMEOUT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JNDI_LDAP_READ_TIMEOUT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_JNDI_LDAP_READ_TIMEOUT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_JNDI_LDAP_READ_TIMEOUT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_CIPHER_SUITES`<br>Use this property to specify the valid cipher suites used while SSL negotiation with LDAP server.                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_LDAP_SSL_CIPHER_SUITES_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_CIPHER_SUITES_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYMANAGER_FACTORY_ALGORITHM`<br>Use this property to override the default algorithm used by KeyManagerFactory.                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYMANAGER_FACTORY_ALGORITHM_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYMANAGER_FACTORY_ALGORITHM_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE`<br>This property is used to specify the KeyStore file path which will be used while SSL negotiation with LDAP server.                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_PASSWORD`<br>This property is used to specify the password for the KeyStore file which will be used while SSL negotiation with LDAP server.                                                                                                                                                                                                                                                                                                                                                                               |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_PASSWORD_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_PASSWORD_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_TYPE`<br>This property is used to specify the type of the KeyStore file which will be used while SSL negotiation with LDAP server.                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_TYPE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_TYPE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTMANAGER_FACTORY_ALGORITHM`<br>Use this property to override the default algorithm used by TrustManagerFactory.                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTMANAGER_FACTORY_ALGORITHM_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTMANAGER_FACTORY_ALGORITHM_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE`<br>This property is used to specify the TrustStore file path which will be used while SSL negotiation with LDAP server.                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_PASSWORD`<br>This property is used to specify the password for the TrustStore file which will be used while SSL negotiation with LDAP server.                                                                                                                                                                                                                                                                                                                                                                           |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_PASSWORD_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_PASSWORD_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_TYPE`<br>This property is used to specify the type of the TrustStore file which will be used while SSL negotiation with LDAP server.                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_TYPE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_TYPE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_VERSIONS`<br>Use this property to specify the valid SSL protocol version(s) used while SSL negotiation with LDAP Server.                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_LDAP_SSL_VERSIONS_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_VERSIONS_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_LOCATION`<br>Use this property to specify the wallet location.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_LOCATION_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_LOCATION_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_PASSWORD`<br>Use this property to specify the password of the wallet file which will be used while SSL negotiation with LDAP server.                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_PASSWORD_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_PASSWORD_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_ALLOW_WEAK_CRYPTO`<br>Starting in release 23, the driver can be configured to use strong session keys and weak ciphers can be disabled when *Native Network Encryption* is used.                                                                                                                                                                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_ALLOW_WEAK_CRYPTO_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_ALLOW_WEAK_CRYPTO_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_JAAS_LOGIN_MODULE`<br>Use this connection property to specify the name of the `JAAS` login module which will be used for initializing `javax.security.auth.login.LoginContext`.                                                                                                                                                                                                                                                                                                                                      |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_JAAS_LOGIN_MODULE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_JAAS_LOGIN_MODULE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_REALM`<br>Use this connection property to specify the realm used for Kerberos authentication.                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_REALM_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_REALM_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_CC_NAME`<br>Use this connection property to specify the location of the Kerberos credential cache.                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_CC_NAME_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_CC_NAME_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_MUTUAL`<br>To turn on Kerberos mutual authentication, set this property to "true".                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_MUTUAL_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_MUTUAL_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_SERVICES`<br>Use this connection property to turn on the authentication adaptors.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_SERVICES_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_SERVICES_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_CHECKSUM_LEVEL`<br>Use this property to specify the level of security for the integrity service.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_CHECKSUM_LEVEL_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_CHECKSUM_LEVEL_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_CHECKSUM_TYPES`<br>Use this connection property to specify the list of integrity algorithms that you want to activate.                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_CHECKSUM_TYPES_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_CHECKSUM_TYPES_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_CONNECT_TIMEOUT`<br>The connect timeout controls how much time is allowed to connect the socket to the database.                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_CONNECT_TIMEOUT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_CONNECT_TIMEOUT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_CRYPTO_SEED`<br>Use this connection property to specify the encryption seed (between 10 and 70 random characters).                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_CRYPTO_SEED_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_CRYPTO_SEED_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_DISABLE_OUT_OF_BAND_BREAK`<br>Thin uses out of band breaks by default from 11g onwards.                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_DISABLE_OUT_OF_BAND_BREAK_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_DISABLE_OUT_OF_BAND_BREAK_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_LEVEL`<br>Use this property to specify the level of security for the encryption service.                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_LEVEL_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_LEVEL_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_TYPES`<br>Use this connection property to specify the list of encryption algorithms that you want to activate.                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_TYPES_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_TYPES_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_OLDSYNTAX`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_OLDSYNTAX_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_OLDSYNTAX_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_PROFILE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_PROFILE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_PROFILE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_USE_ZERO_COPY_IO`<br>The thin driver uses the zero-copy IO codepath for SecureFile Lobs by default from 11gR2 onwards.                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_NET_USE_ZERO_COPY_IO_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_NET_USE_ZERO_COPY_IO_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_OUTBOUND_CONNECT_TIMEOUT`<br>The outbound connect timeout controls the time allowed to connect the socket, let the server accept the connection to the desired service, negotiate the NS protocol as well as complete the ASO negotiation.                                                                                                                                                                                                                                                                                                  |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_OUTBOUND_CONNECT_TIMEOUT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_OUTBOUND_CONNECT_TIMEOUT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_READ_TIMEOUT`<br>Read timeout while reading from the socket.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_READ_TIMEOUT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_READ_TIMEOUT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_SSL_CERTIFICATE_ALIAS`<br>When a keystore (either wallet or jks file) contains multiple certificates, this property can be used to specify the alias name of the certificate to be used by the driver during the client authentication part of the SSL handshake.                                                                                                                                                                                                                                                                           |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_SSL_CERTIFICATE_ALIAS_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_SSL_CERTIFICATE_ALIAS_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_SSL_CIPHER_SUITES`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_SSL_CIPHER_SUITES_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_SSL_CIPHER_SUITES_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_SSL_KEYMANAGERFACTORY_ALGORITHM`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_SSL_KEYMANAGERFACTORY_ALGORITHM_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_SSL_KEYMANAGERFACTORY_ALGORITHM_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_SSL_SERVER_CERT_DN`<br>Use this connection property to specify the distinguished name (DN) of the server used during the SSL handshake to authenticate the server.                                                                                                                                                                                                                                                                                                                                                                          |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_SSL_SERVER_CERT_DN_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_SSL_SERVER_CERT_DN_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_SSL_SERVER_DN_MATCH`<br>Use this connection property to enable or disable the authentication of the server during the SSL handshake.                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_SSL_SERVER_DN_MATCH_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_SSL_SERVER_DN_MATCH_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_SSL_TRUSTMANAGERFACTORY_ALGORITHM`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_SSL_TRUSTMANAGERFACTORY_ALGORITHM_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_SSL_TRUSTMANAGERFACTORY_ALGORITHM_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_SSL_VERSION`<br>Sets the SSL version which will be used for SSL protocol negotiation.<br>This is an optional property.                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_SSL_VERSION_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_SSL_VERSION_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_TCP_NO_DELAY`<br>If the value of this property is "true", the TCP_NODELAY property is set on the socket when using the Thin driver.                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_TCP_NO_DELAY_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_TCP_NO_DELAY_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_USE_JCE_API`<br>If the value of this property is `"true"` and Data Encryption service is enabled, then JDK Crypto(JCE) APIs are used for encryption and decryption of the data between the JDBC client and the Oracle Server, otherwise the built-in crypto implementation is used.                                                                                                                                                                                                                                                         |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_USE_JCE_API_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_USE_JCE_API_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_VSESSION_ENAME`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_VSESSION_ENAME_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_VSESSION_ENAME_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_VSESSION_INAME`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_VSESSION_INAME_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_VSESSION_INAME_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_VSESSION_MACHINE`<br>Use this connection property to change the value that will show up in the "machine" column of the "v\$session" table for this connection.                                                                                                                                                                                                                                                                                                                                                                              |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_VSESSION_MACHINE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_VSESSION_MACHINE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_VSESSION_OSUSER`<br>By default, the driver retrieves the OS username from the "user.name" system property which is set by the JVM.                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_VSESSION_OSUSER_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_VSESSION_OSUSER_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_VSESSION_PROCESS`<br>Use this connection property to change the value that will show up in the "process" column of the "v\$session" table for this connection.                                                                                                                                                                                                                                                                                                                                                                              |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_VSESSION_PROCESS_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_VSESSION_PROCESS_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_VSESSION_PROGRAM`<br>Use this connection property to change the value that will show up in the "program" column of the "v\$session" table for this connection.                                                                                                                                                                                                                                                                                                                                                                              |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_VSESSION_PROGRAM_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_VSESSION_PROGRAM_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_VSESSION_TERMINAL`<br>Use this connection property to change the value that will show up in the "terminal" column of the "v\$session" table for this connection.                                                                                                                                                                                                                                                                                                                                                                            |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_THIN_VSESSION_TERMINAL_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_THIN_VSESSION_TERMINAL_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_TIMESTAMPTZ_IN_GMT`<br>Obtain TIMESTAMP WITH TIME ZONE value in GMT than adjusting the same to local time zone.                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_TIMESTAMPTZ_IN_GMT_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_TIMESTAMPTZ_IN_GMT_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_TIMEZONE_AS_REGION`<br>Use JVM default timezone as specified rather than convert to a GMT offset.                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_TIMEZONE_AS_REGION_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_TIMEZONE_AS_REGION_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_TNS_ADMIN`<br>This property is used for setting the TNS Admin path.                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_TNS_ADMIN_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_TNS_ADMIN_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_TOKEN_AUTHENTICATION`<br>Enables the use of access tokens that are stored in a file system location when authenticating with Oracle Database.                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_TOKEN_AUTHENTICATION_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_TOKEN_AUTHENTICATION_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_TOKEN_LOCATION`<br>When `CONNECTION_PROPERTY_TOKEN_AUTHENTICATION` is set to "OCI_TOKEN" or "OAUTH", this property specifies the file system path to obtain access tokens from.                                                                                                                                                                                                                                                                                                                                                                  |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_TOKEN_LOCATION_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_TOKEN_LOCATION_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_USE_1900_AS_YEAR_FOR_TIME`<br>setTime used to set the date component to 01 Jan, 1900 by default in earlier versions (version \< 10g).                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_USE_1900_AS_YEAR_FOR_TIME_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_USE_1900_AS_YEAR_FOR_TIME_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_USE_DRCP_MULTIPLE_TAG`<br>Enables multiple tagging feature in DRCP.                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_USE_DRCP_MULTIPLE_TAG_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_USE_DRCP_MULTIPLE_TAG_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_USE_FETCH_SIZE_WITH_LONG_COLUMN`<br>If the value of this property is "true", then JDBC will prefetch rows even though there is a LONG or LONG RAW column in the result.                                                                                                                                                                                                                                                                                                                                                                          |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_USE_FETCH_SIZE_WITH_LONG_COLUMN_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_USE_FETCH_SIZE_WITH_LONG_COLUMN_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_USE_THREADLOCAL_BUFFER_CACHE`<br>If true, the statement data buffers are cached on a per thread basis.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_USE_THREADLOCAL_BUFFER_CACHE_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_USE_THREADLOCAL_BUFFER_CACHE_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_USER_NAME`<br>The value of this property is used as the user name when connecting to the database.                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_USER_NAME_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_USER_NAME_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_WALLET_LOCATION`<br>Use this property to specify the wallet location.                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_WALLET_LOCATION_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_WALLET_LOCATION_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_WALLET_PASSWORD`<br>Use this property to set the wallet password which is only required if you don't enable enable auto-login in the wallet.                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_WALLET_PASSWORD_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_WALLET_PASSWORD_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_WEBSOCKET_PASSWORD`<br>This connection property is used to configure the password of the webserver, when the JDBC Thin driver is configured to connect to a webserver using the `Secure Websocket protocol (WSS)`.<br>The webserver acts as a reverse proxy for the Oracle Database.<br>The default value of this property is `null`.<br>                                                                                                                                                                                                        |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_WEBSOCKET_PASSWORD_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_WEBSOCKET_PASSWORD_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_WEBSOCKET_USER`<br>This connection property is used to configure the username of the webserver, when the JDBC Thin driver is configured to connect to a webserver using the `Secure Websocket protocol (WSS)`.<br>The webserver acts as a reverse proxy for the Oracle Database.<br>The default value of this property is `null`.<br>                                                                                                                                                                                                            |
    | `static byte`                                                                                            | `CONNECTION_PROPERTY_WEBSOCKET_USER_ACCESSMODE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `CONNECTION_PROPERTY_WEBSOCKET_USER_DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static int`                                                                                             | `CONNECTION_RELEASE_HIGH`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static int`                                                                                             | `CONNECTION_RELEASE_LOCKED`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static int`                                                                                             | `CONNECTION_RELEASE_LOW`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static int`                                                                                             | `DATABASE_CLOSED`<br>Define return values for pingDatabase api The physical database connection is closed.                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static int`                                                                                             | `DATABASE_NOTOK`<br>Define return values for pingDatabase api The physical database connection is not closed but the database is not reachable.                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static int`                                                                                             | `DATABASE_OK`<br>Define return values for pingDatabase api The physical database connection is not closed and the database is reachable.                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static int`                                                                                             | `DATABASE_TIMEOUT`<br>Define return values for pingDatabase api The call timed out before any positive or negative acknowledgement was received.                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `DCN_BEST_EFFORT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `DCN_CLIENT_INIT_CONNECTION`<br>Set the value of DCN_CLIENT_INIT_CONNECTION to 'true' for using the Client initiated DCN connection.                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `DCN_IGNORE_DELETEOP`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `DCN_IGNORE_INSERTOP`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `DCN_IGNORE_UPDATEOP`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `DCN_NOTIFY_CHANGELAG`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `DCN_NOTIFY_ROWIDS`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `DCN_QUERY_CHANGE_NOTIFICATION`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `DCN_USE_HOST_CONNECTION_ADDR_INFO`<br>Set the value of DCN_USE_HOST_CONNECTION_ADDR_INFO to 'false' to use the address info returned by the server for establishing the client initiated DCN Connection.                                                                                                                                                                                                                                                                                                                                                             |
    | `static int`                                                                                             | `END_TO_END_ACTION_INDEX`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static int`                                                                                             | `END_TO_END_CLIENTID_INDEX`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static int`                                                                                             | `END_TO_END_ECID_INDEX`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static int`                                                                                             | `END_TO_END_MODULE_INDEX`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static int`                                                                                             | `END_TO_END_STATE_INDEX_MAX`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static int`                                                                                             | `INVALID_CONNECTION`<br>Values used for close(int).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NETWORK_COMPRESSION_AUTO`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NETWORK_COMPRESSION_LEVEL_HIGH`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static int`                                                                                             | `NETWORK_COMPRESSION_LEVEL_HIGH_VALUE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NETWORK_COMPRESSION_LEVEL_LOW`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static int`                                                                                             | `NETWORK_COMPRESSION_LEVEL_LOW_VALUE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NETWORK_COMPRESSION_OFF`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NETWORK_COMPRESSION_ON`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static int`                                                                                             | `NETWORK_COMPRESSION_THRESHOLD_MIN`<br>Minimum value supported by the connection property `CONNECTION_PROPERTY_NETWORK_COMPRESSION_THRESHOLD`.                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_AQ_PAYLOAD`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_ASYNC_DEQ`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static int`                                                                                             | `NTF_DEFAULT_TCP_PORT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_GROUPING_CLASS`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_GROUPING_CLASS_NONE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_GROUPING_CLASS_TIME`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_GROUPING_REPEAT_FOREVER`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_GROUPING_REPEAT_TIME`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_GROUPING_START_TIME`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_GROUPING_TYPE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_GROUPING_TYPE_LAST`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_GROUPING_TYPE_SUMMARY`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_GROUPING_VALUE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_LOCAL_HOST`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_LOCAL_TCP_PORT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_QOS_AUTO_ACK`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_QOS_PURGE_ON_NTFN`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_QOS_RELIABLE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_QOS_SECURE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_QOS_TX_ACK`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_TIMEOUT`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `NTF_USE_SSL`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `OCSID_ACTION_KEY`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `OCSID_CLIENTID_KEY`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `OCSID_DBOP_KEY`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `OCSID_ECID_KEY`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `OCSID_MODULE_KEY`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `OCSID_NAMESPACE`<br>Special namespace for sending end-to-end metrics.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `OCSID_SEQUENCE_NUMBER_KEY`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXY_CERTIFICATE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXY_DISTINGUISHED_NAME`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXY_ROLES`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static int`                                                                                             | `PROXY_SESSION`<br>Values used for close(int).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXY_TYPE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXY_USER_NAME`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `PROXY_USER_PASSWORD`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static int`                                                                                             | `PROXYTYPE_CERTIFICATE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static int`                                                                                             | `PROXYTYPE_DISTINGUISHED_NAME`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static int`                                                                                             | `PROXYTYPE_USER_NAME`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static int`                                                                                             | `RELEASE_CONNECTION_CALLBACK`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

    - ### Fields inherited from interface java.sql.[Connection](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)

      [`TRANSACTION_NONE`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#TRANSACTION_NONE)`, `[`TRANSACTION_READ_COMMITTED`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#TRANSACTION_READ_COMMITTED)`, `[`TRANSACTION_READ_UNCOMMITTED`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#TRANSACTION_READ_UNCOMMITTED)`, `[`TRANSACTION_REPEATABLE_READ`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#TRANSACTION_REPEATABLE_READ)`, `[`TRANSACTION_SERIALIZABLE`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#TRANSACTION_SERIALIZABLE)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                                    | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    |----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)               | `_getPC``()`<br>Return the underlying physical connection if this is a logical connection.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                               | `abort``()`<br>Calling abort() on an open connection does the following: marks the connection as closed, closes any sockets or other primitive connections to the database, and insures that any thread that is currently accessing the connection will either progress to completion of the JDBC call or throw an exception.                                                                                                                                                                                                     |
    | `void`                                                                                                               | `addLogicalTransactionIdEventListener``(`[`LogicalTransactionIdEventListener`](LogicalTransactionIdEventListener.md)` listener)`<br>Registers a listener to Logical Transaction Id events.                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                               | `addLogicalTransactionIdEventListener``(`[`LogicalTransactionIdEventListener`](LogicalTransactionIdEventListener.md)` listener, `[`Executor`](http://download.oracle.com/javase/8/docs/api/java/util/concurrent/Executor.html?is-external=true)` executor)`<br>This flavor of `addLogicalTransactionIdEventListener` can be used to register a listener with an executor.                                                                                                                                                         |
    | `void`                                                                                                               | `applyConnectionAttributes``(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` connAttr)`<br>Applies the connection Attributes provided on the underlying PooledConnection.                                                                                                                                                                                                                                                                                               |
    | `void`                                                                                                               | `archive``(int mode, int aseq, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` acstext)`<br>Deprecated. <br>This method will be removed in a future version.                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                                                                                            | `attachServerConnection``()`<br>This method needs to be called before using a DRCP connection.                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `void`                                                                                                               | `beginRequest``()`<br>Declares that a request to the server is starting on this connection.                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `void`                                                                                                               | `cancel``()`<br>Performs an immediate (asynchronous) termination of any currently executing operation on this connection.                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `void`                                                                                                               | `clearAllApplicationContext``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` nameSpace)`<br>Deprecated. <br>This is deprecated since 12.1 in favor of the standard JDBC API setClientInfo(). It is not recommended to use this API intermingled with get/setClientInfo APIs.                                                                                                                                                                                                   |
    | `void`                                                                                                               | `close``(int opt)`<br>If opt is OracleConnection.INVALID_CONNECTION : Closes the given Logical connection, as well the underlying PooledConnection without returning the connection to the cache when called with the parameter INVALID_CONNECTION.                                                                                                                                                                                                                                                                               |
    | `void`                                                                                                               | `close``(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` connAttr)`<br>Closes the given Logical connection, and returns the underlying PooledConnection to the implicit connection cache.                                                                                                                                                                                                                                                                               |
    | `void`                                                                                                               | `commit``(`[`EnumSet`](http://download.oracle.com/javase/8/docs/api/java/util/EnumSet.html?is-external=true)`<`[`OracleConnection.CommitOption`](OracleConnection.CommitOption.md)`> options)`<br>Commits the transaction with the given options.                                                                                                                                                                                                                                                                                 |
    | [`ARRAY`](../sql/ARRAY.md)                                                                                           | `createARRAY``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` elements)`<br>Creates an ARRAY object with the given type name and elements.                                                                                                                                                                                                                         |
    | [`BINARY_DOUBLE`](../sql/BINARY_DOUBLE.md)                                                                           | `createBINARY_DOUBLE``(double value)`<br>Creates a BINARY_DOUBLE that has the given value.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | [`BINARY_FLOAT`](../sql/BINARY_FLOAT.md)                                                                             | `createBINARY_FLOAT``(float value)`<br>Creates a BINARY_FLOAT that has the given value.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`DATE`](../sql/DATE.md)                                                                                             | `createDATE``(`[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` value)`<br>Creates a DATE that has the given value.                                                                                                                                                                                                                                                                                                                                                                    |
    | [`DATE`](../sql/DATE.md)                                                                                             | `createDATE``(`[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Creates a DATE that has the given value.                                                                                                                                                                                                                                                         |
    | [`DATE`](../sql/DATE.md)                                                                                             | `createDATE``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Creates a DATE that has the given value.                                                                                                                                                                                                                                                                                                                                                               |
    | [`DATE`](../sql/DATE.md)                                                                                             | `createDATE``(`[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` value)`<br>Creates a DATE that has the given value.                                                                                                                                                                                                                                                                                                                                                                    |
    | [`DATE`](../sql/DATE.md)                                                                                             | `createDATE``(`[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Creates a DATE that has the given value.                                                                                                                                                                                                                                                         |
    | [`DATE`](../sql/DATE.md)                                                                                             | `createDATE``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` value)`<br>Creates a DATE that has the given value.                                                                                                                                                                                                                                                                                                                                                          |
    | [`DATE`](../sql/DATE.md)                                                                                             | `createDATE``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Creates a DATE that has the given value.                                                                                                                                                                                                                                               |
    | [`INTERVALDS`](../sql/INTERVALDS.md)                                                                                 | `createINTERVALDS``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Creates an INTERVALDS that has the given value.                                                                                                                                                                                                                                                                                                                                                  |
    | [`INTERVALYM`](../sql/INTERVALYM.md)                                                                                 | `createINTERVALYM``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Creates an INTERVALYM that has the given value.                                                                                                                                                                                                                                                                                                                                                  |
    | [`NUMBER`](../sql/NUMBER.md)                                                                                         | `createNUMBER``(`[`BigDecimal`](http://download.oracle.com/javase/8/docs/api/java/math/BigDecimal.html?is-external=true)` value)`<br>Creates a new NUMBER that has the given value.                                                                                                                                                                                                                                                                                                                                               |
    | [`NUMBER`](../sql/NUMBER.md)                                                                                         | `createNUMBER``(`[`BigInteger`](http://download.oracle.com/javase/8/docs/api/java/math/BigInteger.html?is-external=true)` value)`<br>Creates a new NUMBER that has the given value.                                                                                                                                                                                                                                                                                                                                               |
    | [`NUMBER`](../sql/NUMBER.md)                                                                                         | `createNUMBER``(boolean value)`<br>Creates a new NUMBER that has the given value.                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | [`NUMBER`](../sql/NUMBER.md)                                                                                         | `createNUMBER``(byte value)`<br>Creates a new NUMBER that has the given value.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`NUMBER`](../sql/NUMBER.md)                                                                                         | `createNUMBER``(double value)`<br>Creates a new NUMBER that has the given value.                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | [`NUMBER`](../sql/NUMBER.md)                                                                                         | `createNUMBER``(float value)`<br>Creates a new NUMBER that has the given value.                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | [`NUMBER`](../sql/NUMBER.md)                                                                                         | `createNUMBER``(int value)`<br>Creates a new NUMBER that has the given value.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | [`NUMBER`](../sql/NUMBER.md)                                                                                         | `createNUMBER``(long value)`<br>Creates a new NUMBER that has the given value.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`NUMBER`](../sql/NUMBER.md)                                                                                         | `createNUMBER``(short value)`<br>Creates a new NUMBER that has the given value.                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | [`NUMBER`](../sql/NUMBER.md)                                                                                         | `createNUMBER``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value, int scale)`<br>Creates a new NUMBER that has the given value and scale.                                                                                                                                                                                                                                                                                                                                  |
    | [`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)                         | `createOracleArray``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` arrayTypeName, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` elements)`<br>Creates an Array object with the given type name and elements.                                                                                                                                                                                                              |
    | [`TIMESTAMP`](../sql/TIMESTAMP.md)                                                                                   | `createTIMESTAMP``(`[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` value)`<br>Creates a new TIMESTAMP with the given value.                                                                                                                                                                                                                                                                                                                                                          |
    | [`TIMESTAMP`](../sql/TIMESTAMP.md)                                                                                   | `createTIMESTAMP``(`[`DATE`](../sql/DATE.md)` value)`<br>Creates a new TIMESTAMP with the given value.                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`TIMESTAMP`](../sql/TIMESTAMP.md)                                                                                   | `createTIMESTAMP``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Creates a new TIMESTAMP with the given value.                                                                                                                                                                                                                                                                                                                                                     |
    | [`TIMESTAMP`](../sql/TIMESTAMP.md)                                                                                   | `createTIMESTAMP``(`[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` value)`<br>Creates a new TIMESTAMP with the given value.                                                                                                                                                                                                                                                                                                                                                          |
    | [`TIMESTAMP`](../sql/TIMESTAMP.md)                                                                                   | `createTIMESTAMP``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` value)`<br>Creates a new TIMESTAMP with the given value.                                                                                                                                                                                                                                                                                                                                                |
    | [`TIMESTAMP`](../sql/TIMESTAMP.md)                                                                                   | `createTIMESTAMP``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Creates a new TIMESTAMP with the given value.                                                                                                                                                                                                                                     |
    | [`TIMESTAMPLTZ`](../sql/TIMESTAMPLTZ.md)                                                                             | `createTIMESTAMPLTZ``(`[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Creates a new TIMESTAMPLTZ with the given value.                                                                                                                                                                                                                                         |
    | [`TIMESTAMPLTZ`](../sql/TIMESTAMPLTZ.md)                                                                             | `createTIMESTAMPLTZ``(`[`DATE`](../sql/DATE.md)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Creates a new TIMESTAMPLTZ with the given value.                                                                                                                                                                                                                                                                                                           |
    | [`TIMESTAMPLTZ`](../sql/TIMESTAMPLTZ.md)                                                                             | `createTIMESTAMPLTZ``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Creates a new TIMESTAMPLTZ with the given value.                                                                                                                                                                                                                                    |
    | [`TIMESTAMPLTZ`](../sql/TIMESTAMPLTZ.md)                                                                             | `createTIMESTAMPLTZ``(`[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Creates a new TIMESTAMPLTZ with the given value.                                                                                                                                                                                                                                         |
    | [`TIMESTAMPLTZ`](../sql/TIMESTAMPLTZ.md)                                                                             | `createTIMESTAMPLTZ``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Creates a new TIMESTAMPLTZ with the given value.                                                                                                                                                                                                                               |
    | [`TIMESTAMPTZ`](../sql/TIMESTAMPTZ.md)                                                                               | `createTIMESTAMPTZ``(`[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` value)`<br>Creates a new TIMESTAMPTZ with the given value.                                                                                                                                                                                                                                                                                                                                                      |
    | [`TIMESTAMPTZ`](../sql/TIMESTAMPTZ.md)                                                                               | `createTIMESTAMPTZ``(`[`DATE`](../sql/DATE.md)` value)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`TIMESTAMPTZ`](../sql/TIMESTAMPTZ.md)                                                                               | `createTIMESTAMPTZ``(`[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Creates a new TIMESTAMPTZ with the given value.                                                                                                                                                                                                                                           |
    | [`TIMESTAMPTZ`](../sql/TIMESTAMPTZ.md)                                                                               | `createTIMESTAMPTZ``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Creates a new TIMESTAMPTZ with the given value.                                                                                                                                                                                                                                                                                                                                                 |
    | [`TIMESTAMPTZ`](../sql/TIMESTAMPTZ.md)                                                                               | `createTIMESTAMPTZ``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Creates a new TIMESTAMPTZ with the given value.                                                                                                                                                                                                                                      |
    | [`TIMESTAMPTZ`](../sql/TIMESTAMPTZ.md)                                                                               | `createTIMESTAMPTZ``(`[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` value)`<br>Creates a new TIMESTAMPTZ with the given value.                                                                                                                                                                                                                                                                                                                                                      |
    | [`TIMESTAMPTZ`](../sql/TIMESTAMPTZ.md)                                                                               | `createTIMESTAMPTZ``(`[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Creates a new TIMESTAMPTZ with the given value.                                                                                                                                                                                                                                           |
    | [`TIMESTAMPTZ`](../sql/TIMESTAMPTZ.md)                                                                               | `createTIMESTAMPTZ``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` value)`<br>Creates a new TIMESTAMPTZ with the given value.                                                                                                                                                                                                                                                                                                                                            |
    | [`TIMESTAMPTZ`](../sql/TIMESTAMPTZ.md)                                                                               | `createTIMESTAMPTZ``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Creates a new TIMESTAMPTZ with the given value.                                                                                                                                                                                                                                 |
    | [`TIMESTAMPTZ`](../sql/TIMESTAMPTZ.md)                                                                               | `createTIMESTAMPTZ``(`[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` value, java.time.ZoneId tzid)`<br>Creates a new TIMESTAMPTZ with the given value.                                                                                                                                                                                                                                                                                                                     |
    | [`AQMessage`](aq/AQMessage.md)                                                                                       | `dequeue``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQDequeueOptions`](aq/AQDequeueOptions.md)` opt, byte[] tdo)`<br>Dequeues an AQ message from the queue specified by its name.                                                                                                                                                                                                                                                                          |
    | [`AQMessage`](aq/AQMessage.md)                                                                                       | `dequeue``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQDequeueOptions`](aq/AQDequeueOptions.md)` opt, byte[] tdo, int version)`<br>Dequeues an AQ message from the queue specified by its name.                                                                                                                                                                                                                                                             |
    | [`AQMessage`](aq/AQMessage.md)                                                                                       | `dequeue``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQDequeueOptions`](aq/AQDequeueOptions.md)` opt, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName)`<br>Dequeues an AQ message from the queue specified by its name.                                                                                                                                                                          |
    | `void`                                                                                                               | `detachServerConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` tag)`<br>Notify the server that this connection will not be used.                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                                                                                               | `endRequest``()`<br>Declares that the request that was in progress on this connection has completed.                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                               | `enqueue``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` queueName, `[`AQEnqueueOptions`](aq/AQEnqueueOptions.md)` opt, `[`AQMessage`](aq/AQMessage.md)` mesg)`<br>Enqueues the given AQ message to the queue specified by its name.                                                                                                                                                                                                                                          |
    | [`TypeDescriptor`](../sql/TypeDescriptor.md)`[]`                                                                     | `getAllTypeDescriptorsInCurrentSchema``()`<br>Obtain all the type descriptors associated with object types or array in the schema of this connection.                                                                                                                                                                                                                                                                                                                                                                             |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getAuthenticationAdaptorName``()`<br>Returns the name of the adaptor that is used for authentication by the thin driver.                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `boolean`                                                                                                            | `getAutoClose``()`<br>The driver is always in auto-close mode.                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true) | `getCallWithKey``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key)`<br>getCallWithKey Searches the explicit cache for a match on key.                                                                                                                                                                                                                                                                                                                                       |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getChecksumProviderName``()`<br>If network integrity service is enabled, returns the name of the checksum provider, otherwise returns `null`.                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)              | `getConnectionAttributes``()`<br>Returns the connection Attributes set on the underlying PooledConnection.                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `int`                                                                                                                | `getConnectionReleasePriority``()`<br>Returns the release priority set on the connection                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `boolean`                                                                                                            | `getCreateStatementAsRefCursor``()`<br>Retrieves the current setting of the `createStatementAsRefCursor` flag which you can set with the `setCreateStatementAsRefCursor` method.                                                                                                                                                                                                                                                                                                                                                  |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getCurrentSchema``()`<br>Obtains the current schema of the current connection.                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | [`DatabaseChangeRegistration`](dcn/DatabaseChangeRegistration.md)                                                    | `getDatabaseChangeRegistration``(int regid)`<br>Maps an existing registration identified by its ID 'regid' with a new DatabaseChangeRegistration object.                                                                                                                                                                                                                                                                                                                                                                          |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getDataIntegrityAlgorithmName``()`<br>Returns the name of the algorithm that is used for data integrity checking by the thin driver on the network.                                                                                                                                                                                                                                                                                                                                                                              |
    | `int`                                                                                                                | `getDefaultExecuteBatch``()`<br>Deprecated. <br>As of 12.1 all APIs related to oracle-style statement batching are deprecated in favor of standard JDBC batching. We recommend using the standard model going forward as it is spec compliant and provides more information and control to the application.                                                                                                                                                                                                                       |
    | `int`                                                                                                                | `getDefaultRowPrefetch``()`<br>Retrieves the value of row prefetch for all statements associated with this connection and created after this value was set.                                                                                                                                                                                                                                                                                                                                                                       |
    | [`TimeZone`](http://download.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)                  | `getDefaultTimeZone``()`<br>Returns the TimeZone set through setDefaultTimeZone.                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                      | `getDescriptor``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql_name)`<br>Gets a Descriptor object corresponding to a sql type.                                                                                                                                                                                                                                                                                                                                            |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getDRCPPLSQLCallbackName``()`<br>Returns the PL/SQL Fix-up callback name if configured, otherwise returns `Null`                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getDRCPReturnTag``()`<br>Returns the tag associated with this DRCP pooled server.                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | [`OracleConnection.DRCPState`](OracleConnection.DRCPState.md)                                                        | `getDRCPState``()`<br>Returns an enum indicating if the connection is attached to a DRCP server process.                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getEncryptionAlgorithmName``()`<br>Returns the name of the algorithm that is used for data encryption by the thin driver on the network.                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getEncryptionProviderName``()`<br>If network encryption service is enabled, returns the name of the encryption provider, otherwise returns `null`.                                                                                                                                                                                                                                                                                                                                                                               |
    | `short`                                                                                                              | `getEndToEndECIDSequenceNumber``()`<br>Deprecated. <br>This is deprecated since 12.1 in favor of getClientInfo(). It is not recommended to use this API intermingled with get/setClientInfo APIs.                                                                                                                                                                                                                                                                                                                                 |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`                  | `getEndToEndMetrics``()`<br>Deprecated. <br>This has been deprecated since 12.1 in favor of getClientInfo(). It is not recommended to use this API intermingled with get/setClientInfo APIs.                                                                                                                                                                                                                                                                                                                                      |
    | `boolean`                                                                                                            | `getExplicitCachingEnabled``()`<br>getExplicitCachingEnabled Returns true if the explicit cache is currently enabled, false otherwise.                                                                                                                                                                                                                                                                                                                                                                                            |
    | `boolean`                                                                                                            | `getImplicitCachingEnabled``()`<br>getImplicitCachingEnabled Returns true if the implicit cache is currently enabled, false otherwise.                                                                                                                                                                                                                                                                                                                                                                                            |
    | `boolean`                                                                                                            | `getIncludeSynonyms``()`<br>Checks whether or not synonyms information is included in `DatabaseMetaData.getColumns`.                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                      | `getJavaObject``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql_name)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`LogicalTransactionId`](LogicalTransactionId.md)                                                                    | `getLogicalTransactionId``()`<br>Gets the current Logical Transaction Id which are sent by the server in a piggy back message and hence this method call doesn't make a roundtrip.                                                                                                                                                                                                                                                                                                                                                |
    | [`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)              | `getProperties``()`<br>Determines the connection properties.                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `boolean`                                                                                                            | `getRemarksReporting``()`<br>Checks whether or not a call of `getTables` or `getColumns` of the `DatabaseMetaData` interface will report the `REMARKS` column.                                                                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                                                                                            | `getRestrictGetTables``()`<br>Gets the restriction status of the returned data in `DatabaseMetaData.getTables`.                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getSessionTimeZone``()`<br>Obtain Oracle session time zone region name.                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getSessionTimeZoneOffset``()`<br>Obtain the time zone offset in hours of the current database session.                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getSQLType``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                              |
    | `int`                                                                                                                | `getStatementCacheSize``()`<br>getStatementCacheSize Returns the current size of the application cache.                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true) | `getStatementWithKey``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key)`<br>getStatementWithKey Searches the explicit cache for a match on key.                                                                                                                                                                                                                                                                                                                             |
    | `int`                                                                                                                | `getStmtCacheSize``()`<br>Deprecated. <br>Use getStatementCacheSize() instead.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `short`                                                                                                              | `getStructAttrCsId``()`<br>Obtain the Oracle identifier of the character set used in STRUCT attributes.                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`TypeDescriptor`](../sql/TypeDescriptor.md)`[]`                                                                     | `getTypeDescriptorsFromList``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[][] schemaAndTypeNamePairs)`<br>Obtain the type descriptors associated with object types or arrays from an array of scheama and type names.                                                                                                                                                                                                                                                       |
    | [`TypeDescriptor`](../sql/TypeDescriptor.md)`[]`                                                                     | `getTypeDescriptorsFromListInCurrentSchema``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] typeNames)`<br>Obtain the type descriptors associated with object types or array in a schema from an array of type names.                                                                                                                                                                                                                                                        |
    | [`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)              | `getUnMatchedConnectionAttributes``()`<br>Returns the unmatched connection Attributes from the underlying PooledConnection.                                                                                                                                                                                                                                                                                                                                                                                                       |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getUserName``()`<br>Gets the user name of the current connection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `boolean`                                                                                                            | `getUsingXAFlag``()`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `boolean`                                                                                                            | `getXAErrorFlag``()`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `boolean`                                                                                                            | `isDRCPEnabled``()`<br>Returns `true` if the connection is participating in DRCP.                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                                                                                            | `isDRCPMultitagEnabled``()`<br>Returns true if multiple tags are allowed with DRCP Connection.                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                                                                                            | `isLogicalConnection``()`<br>Method that returns a boolean indicating whether its a logical connection or not.                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                                                                                            | `isProxySession``()`<br>Returns true if the current session associated with this connection is a proxy session.                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `boolean`                                                                                                            | `isUsable``()`<br>Identifies whether this connection is still usable for JDBC operations.                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `boolean`                                                                                                            | `isValid``(`[`OracleConnection.ConnectionValidation`](OracleConnection.ConnectionValidation.md)` effort, int timeout)`<br>Returns true if this connection was working properly to the extent specified by `effort` at the instant during this call it was checked.                                                                                                                                                                                                                                                                |
    | `boolean`                                                                                                            | `needToPurgeStatementCache``()`<br>Returns if the client side Statement cache has to be purged.                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                                                                                               | `openProxySession``(int type, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` prop)`<br>Opens a new proxy session with the username provided in the prop argument and switches to this new session.<br><br>This feature is supported for both thin and oci driver.<br><br>Three proxy types are supported :<br>OracleConnection.PROXYTYPE_USER_NAME : In this type PROXY_USER_NAME needs to be provided in prop.                                                        |
    | `void`                                                                                                               | `oracleReleaseSavepoint``(`[`OracleSavepoint`](OracleSavepoint.md)` savepoint)`<br>Removes the given `OracleSavepoint` object from the current transaction.                                                                                                                                                                                                                                                                                                                                                                       |
    | `void`                                                                                                               | `oracleRollback``(`[`OracleSavepoint`](OracleSavepoint.md)` savepoint)`<br>Undoes all changes made after the given `OracleSavepoint` object was set.                                                                                                                                                                                                                                                                                                                                                                              |
    | [`OracleSavepoint`](OracleSavepoint.md)                                                                              | `oracleSetSavepoint``()`<br>Creates an unnamed savepoint in the current transaction and returns the new `OracleSavepoint` object that represents it.                                                                                                                                                                                                                                                                                                                                                                              |
    | [`OracleSavepoint`](OracleSavepoint.md)                                                                              | `oracleSetSavepoint``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Creates a savepoint with the given name in the current transaction and returns the new `OracleSavepoint` object that represents it.                                                                                                                                                                                                                                                             |
    | `int`                                                                                                                | `pingDatabase``()`<br>Ping Database server to see if both database and the connection are actively up.                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `int`                                                                                                                | `pingDatabase``(int timeOut)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true) | `prepareCallWithKey``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key)`<br>Deprecated. <br>This is same as prepareCall, except if a Callable Statement with the given KEY exists in the Cache, then the statement is returned AS IT IS when it was closed and cached with this KEY. An object returned from the Cache based on Key will have its state set to "KEYED". If no such Callable Statement is found, then null is returned. Key cannot be null.                   |
    | [`PreparedStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true) | `prepareStatementWithKey``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key)`<br>Deprecated. <br>This is same as prepareStatement, except if a Prepared Statement with the given KEY exists in the Cache, then the statement is returned AS IT IS when it was closed and cached with this KEY. An object returned from the Cache based on Key will have its state set to "KEYED". If no such Prepared Statement is found, a null is returned. Key cannot be null.            |
    | `void`                                                                                                               | `purgeExplicitCache``()`<br>purgeExplicitCache Removes all existing statements from the explicit cache, after which it will be empty.                                                                                                                                                                                                                                                                                                                                                                                             |
    | `void`                                                                                                               | `purgeImplicitCache``()`<br>purgeImplicitCache Removes all existing statements from the implicit cache, after which it will be empty.                                                                                                                                                                                                                                                                                                                                                                                             |
    | `void`                                                                                                               | `putDescriptor``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql_name, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` desc)`<br>Store the Object Descriptor for later usage.                                                                                                                                                                                                                                             |
    | [`AQNotificationRegistration`](aq/AQNotificationRegistration.md)`[]`                                                 | `registerAQNotification``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] name, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)`[] options, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` globaloptions)`<br>Registers your interest into being notified when a message is enqueued in a particular queue (or array of queues).                          |
    | `void`                                                                                                               | `registerConnectionCacheCallback``(`[`OracleConnectionCacheCallback`](pool/OracleConnectionCacheCallback.md)` occc, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` userObj, int cbkFlag)`<br>Registers the connection cache callback on the logical connection This is used in conjunction with the Implicit Connection Cache Properties.                                                                                                                                      |
    | [`DatabaseChangeRegistration`](dcn/DatabaseChangeRegistration.md)                                                    | `registerDatabaseChangeNotification``(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` options)`<br>Creates a new database change registration.                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                               | `registerSQLType``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql_name, `[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` java_class)`<br>Deprecated.                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                               | `registerSQLType``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sql_name, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` java_class_name)`<br>Deprecated.                                                                                                                                                                                                                                                                 |
    | `void`                                                                                                               | `registerTAFCallback``(`[`OracleOCIFailover`](OracleOCIFailover.md)` cbk, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Register an application TAF Callback instance that will be called when an application failover occurs.                                                                                                                                                                                                                                       |
    | `void`                                                                                                               | `removeLogicalTransactionIdEventListener``(`[`LogicalTransactionIdEventListener`](LogicalTransactionIdEventListener.md)` listener)`<br>Deregisters the Logical Transaction Id event listener.                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                                                                                               | `setApplicationContext``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` nameSpace, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` attribute, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Deprecated. <br>This has been deprecated since 12.1 in favour of setClientInfo(). It is not recommended to use this API intermingled with get/setClientInfo APIs. |
    | `void`                                                                                                               | `setAutoClose``(boolean autoClose)`<br>set auto-close mode.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `void`                                                                                                               | `setConnectionReleasePriority``(int priority)`<br>Sets connection release priority.                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `void`                                                                                                               | `setCreateStatementAsRefCursor``(boolean value)`<br>When this is set to `true`, any new statements created from this connection will be created as a `REF CURSOR`.                                                                                                                                                                                                                                                                                                                                                                |
    | `void`                                                                                                               | `setDefaultExecuteBatch``(int batch)`<br>Deprecated. <br>As of 12.1 all APIs related to oracle-style statement batching are deprecated in favor of standard JDBC batching. We recommend using the standard model going forward as it is spec compliant and provides more information and control to the application.                                                                                                                                                                                                              |
    | `void`                                                                                                               | `setDefaultRowPrefetch``(int value)`<br>Sets the value of row prefetch for all statements associated with this connection and created after this value was set.                                                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                                                                                               | `setDefaultTimeZone``(`[`TimeZone`](http://download.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)` tz)`<br>The TimeZone to be used while creating java.sql.Date, java.sql.Time & java.sql.Timestamp.                                                                                                                                                                                                                                                                                                     |
    | `void`                                                                                                               | `setEndToEndMetrics``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] metrics, short sequenceNumber)`<br>Deprecated. <br>It has been deprecated since 12.1 in favor of setClientInfo(). It is not recommended to use this API intermingled with get/setClientInfo APIs.                                                                                                                                                                                                       |
    | `void`                                                                                                               | `setExplicitCachingEnabled``(boolean cache)`<br>setExplicitCachingEnabled Enables or disables the explicit cache.                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `void`                                                                                                               | `setImplicitCachingEnabled``(boolean cache)`<br>setImplicitCachingEnabled Enables or disables the implicit cache.                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `void`                                                                                                               | `setIncludeSynonyms``(boolean synonyms)`<br>Turns on or off retrieval of synonym information in DatabaseMetaData.                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `void`                                                                                                               | `setPlsqlWarnings``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` setting)`<br>Enable/Disable PLSQL Compiler Warnings                                                                                                                                                                                                                                                                                                                                                         |
    | `void`                                                                                                               | `setRemarksReporting``(boolean reportRemarks)`<br>Turns on or off the reporting of the REMARKS columns by the `getTables` and `getColumns` calls of the `DatabaseMetaData` interface.                                                                                                                                                                                                                                                                                                                                             |
    | `void`                                                                                                               | `setRestrictGetTables``(boolean restrict)`<br>Turns on or off the restriction of the returned data in `DatabaseMetaData.getTables.`                                                                                                                                                                                                                                                                                                                                                                                               |
    | `void`                                                                                                               | `setSessionTimeZone``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` regionName)`<br>Set the session time zone.                                                                                                                                                                                                                                                                                                                                                                |
    | `void`                                                                                                               | `setShardingKey``(`[`OracleShardingKey`](OracleShardingKey.md)` shardingKey)`<br>Sets the sharding key on this connection.                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                               | `setShardingKey``(`[`OracleShardingKey`](OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](OracleShardingKey.md)` superShardingKey)`<br>Sets the sharding key and the super sharding key on this connection.                                                                                                                                                                                                                                                                                                             |
    | `boolean`                                                                                                            | `setShardingKeyIfValid``(`[`OracleShardingKey`](OracleShardingKey.md)` shardingKey, int timeout)`<br>Checks the validity of the connection and also checks if the sharding key passed to this method is valid for the connection.If the sharding key is valid, it will be set on the connection.                                                                                                                                                                                                                                  |
    | `boolean`                                                                                                            | `setShardingKeyIfValid``(`[`OracleShardingKey`](OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](OracleShardingKey.md)` superShardingKey, int timeout)`<br>Checks the validity of the connection and also checks if the sharding keys passed to this method are valid for the connection.If the sharding keys are valid, it will be set on the connection.                                                                                                                                                              |
    | `void`                                                                                                               | `setStatementCacheSize``(int size)`<br>setStatementCacheSize Specifies the size of the size of the application cache (which will be used by both implicit and explicit caching).                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                               | `setStmtCacheSize``(int size)`<br>Deprecated. <br>Use setStatementCacheSize() instead.                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `void`                                                                                                               | `setStmtCacheSize``(int size, boolean clearMetaData)`<br>Deprecated. <br>Use setStatementCacheSize() instead.                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                                                                                               | `setUsingXAFlag``(boolean value)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                               | `setWrapper``(OracleConnection wrapper)`<br>Set the wrapping object.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                               | `setXAErrorFlag``(boolean value)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                               | `shutdown``(`[`OracleConnection.DatabaseShutdownMode`](OracleConnection.DatabaseShutdownMode.md)` mode)`<br>Shuts the database server down.                                                                                                                                                                                                                                                                                                                                                                                       |
    | `void`                                                                                                               | `startup``(`[`OracleConnection.DatabaseStartupMode`](OracleConnection.DatabaseStartupMode.md)` mode)`<br>Starts the database server up.                                                                                                                                                                                                                                                                                                                                                                                           |
    | `void`                                                                                                               | `startup``(`[`OracleConnection.DatabaseStartupMode`](OracleConnection.DatabaseStartupMode.md)` mode, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pfileName)`<br>Starts the database server up.                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                               | `startup``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` startup_str, int mode)`<br>Deprecated. <br>This method will be removed in a future version.                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                               | `unregisterAQNotification``(`[`AQNotificationRegistration`](aq/AQNotificationRegistration.md)` registration)`<br>Deletes a given AQ registration.                                                                                                                                                                                                                                                                                                                                                                                 |
    | `void`                                                                                                               | `unregisterDatabaseChangeNotification``(`[`DatabaseChangeRegistration`](dcn/DatabaseChangeRegistration.md)` registration)`<br>Deletes a given database change registration.                                                                                                                                                                                                                                                                                                                                                       |
    | `void`                                                                                                               | `unregisterDatabaseChangeNotification``(int registrationId)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `void`                                                                                                               | `unregisterDatabaseChangeNotification``(int registrationId, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` host, int tcpport)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                               | `unregisterDatabaseChangeNotification``(long registrationId, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` callback)`<br>Deletes a given database change registration in the server.                                                                                                                                                                                                                                                                                          |
    | `OracleConnection`                                                                                                   | `unwrap``()`<br>Return the wrapped object if any else null.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

    - ### Methods inherited from interface java.sql.[Connection](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)

      [`abort`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#abort_java_util_concurrent_Executor_)`, `[`clearWarnings`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#clearWarnings__)`, `[`close`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#close__)`, `[`commit`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#commit__)`, `[`createArrayOf`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createArrayOf_java_lang_String_java_lang_Object_A_)`, `[`createBlob`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createBlob__)`, `[`createClob`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createClob__)`, `[`createNClob`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createNClob__)`, `[`createSQLXML`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createSQLXML__)`, `[`createStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createStatement__)`, `[`createStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createStatement_int_int_)`, `[`createStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createStatement_int_int_int_)`, `[`createStruct`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createStruct_java_lang_String_java_lang_Object_A_)`, `[`getAutoCommit`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#getAutoCommit__)`, `[`getCatalog`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#getCatalog__)`, `[`getClientInfo`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#getClientInfo__)`, `[`getClientInfo`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#getClientInfo_java_lang_String_)`, `[`getHoldability`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#getHoldability__)`, `[`getMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#getMetaData__)`, `[`getNetworkTimeout`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#getNetworkTimeout__)`, `[`getSchema`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#getSchema__)`, `[`getTransactionIsolation`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#getTransactionIsolation__)`, `[`getTypeMap`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#getTypeMap__)`, `[`getWarnings`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#getWarnings__)`, `[`isClosed`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#isClosed__)`, `[`isReadOnly`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#isReadOnly__)`, `[`isValid`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#isValid_int_)`, `[`nativeSQL`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#nativeSQL_java_lang_String_)`, `[`prepareCall`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareCall_java_lang_String_)`, `[`prepareCall`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareCall_java_lang_String_int_int_)`, `[`prepareCall`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareCall_java_lang_String_int_int_int_)`, `[`prepareStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareStatement_java_lang_String_)`, `[`prepareStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareStatement_java_lang_String_int_)`, `[`prepareStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareStatement_java_lang_String_int_A_)`, `[`prepareStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareStatement_java_lang_String_int_int_)`, `[`prepareStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareStatement_java_lang_String_int_int_int_)`, `[`prepareStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#prepareStatement_java_lang_String_java_lang_String_A_)`, `[`releaseSavepoint`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#releaseSavepoint_java_sql_Savepoint_)`, `[`rollback`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#rollback__)`, `[`rollback`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#rollback_java_sql_Savepoint_)`, `[`setAutoCommit`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setAutoCommit_boolean_)`, `[`setCatalog`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setCatalog_java_lang_String_)`, `[`setClientInfo`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setClientInfo_java_util_Properties_)`, `[`setClientInfo`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setClientInfo_java_lang_String_java_lang_String_)`, `[`setHoldability`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setHoldability_int_)`, `[`setNetworkTimeout`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setNetworkTimeout_java_util_concurrent_Executor_int_)`, `[`setReadOnly`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setReadOnly_boolean_)`, `[`setSavepoint`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setSavepoint__)`, `[`setSavepoint`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setSavepoint_java_lang_String_)`, `[`setSchema`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setSchema_java_lang_String_)`, `[`setTransactionIsolation`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setTransactionIsolation_int_)`, `[`setTypeMap`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setTypeMap_java_util_Map_)

    <!-- -->

    - ### Methods inherited from interface java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      [`isWrapperFor`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#isWrapperFor_java_lang_Class_)`, `[`unwrap`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#unwrap_java_lang_Class_)

<!-- -->

- - ### Field Detail

    - #### ACCESSMODE_JAVAPROP

          static final byte ACCESSMODE_JAVAPROP

      Bitmask which can be applied to the `CONNECTION_PROPERTY_{name}_ACCESSMODE` constants defined in this interface.
      Indicates that the driver will read a connection property from a Properties object.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ACCESSMODE_SYSTEMPROP

          static final byte ACCESSMODE_SYSTEMPROP

      Bitmask which can be applied to the `CONNECTION_PROPERTY_{name}_ACCESSMODE` constants defined in this interface.
      Indicates that the driver will read a connection property from the JVM's system properties.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ACCESSMODE_BOTH

          static final byte ACCESSMODE_BOTH

      Bitmask which can be applied to the `CONNECTION_PROPERTY_{name}_ACCESSMODE` constants defined in this interface.
      Indicates that the driver will read a connection property from either a Properties object or the JVM's system properties. If a property is defined in both sources, the value given by the Properties object takes precedence.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ACCESSMODE_FILEPROP

          static final byte ACCESSMODE_FILEPROP

      Bitmask which can be applied to the `CONNECTION_PROPERTY_{name}_ACCESSMODE` constants defined in this interface.
      Indicates that the driver will read a connection property from a properties file.
      See Also:
      `CONNECTION_PROPERTY_CONFIG_FILE`, [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_RETAIN_V9_BIND_BEHAVIOR

          static final String CONNECTION_PROPERTY_RETAIN_V9_BIND_BEHAVIOR

      This is applicable only for the thin driver. Pass "true" to retain the V9 bind behavior for Long and potential long binds. "false" is the default behavior which would emulate the same behavior as in OCI driver.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_RETAIN_V9_BIND_BEHAVIOR_DEFAULT

          static final String CONNECTION_PROPERTY_RETAIN_V9_BIND_BEHAVIOR_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_RETAIN_V9_BIND_BEHAVIOR_ACCESSMODE

          static final byte CONNECTION_PROPERTY_RETAIN_V9_BIND_BEHAVIOR_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_USER_NAME

          static final String CONNECTION_PROPERTY_USER_NAME

      The value of this property is used as the user name when connecting to the database. Note that there are other ways to set the username: in the URL or in a wallet but the value of this property overwrites any other value.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_USER_NAME_DEFAULT

          static final String CONNECTION_PROPERTY_USER_NAME_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_USER_NAME_ACCESSMODE

          static final byte CONNECTION_PROPERTY_USER_NAME_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_NEW_PASSWORD

          static final String CONNECTION_PROPERTY_NEW_PASSWORD

      This property enables users to set a new password during connection creation if user's password got expired. User can also change the password using this property even if their password is not expired.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_NEW_PASSWORD_DEFAULT

          static final String CONNECTION_PROPERTY_NEW_PASSWORD_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_NEW_PASSWORD_ACCESSMODE

          static final byte CONNECTION_PROPERTY_NEW_PASSWORD_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DATABASE

          static final String CONNECTION_PROPERTY_DATABASE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DATABASE_DEFAULT

          static final String CONNECTION_PROPERTY_DATABASE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_DATABASE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_DATABASE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_AUTOCOMMIT

          static final String CONNECTION_PROPERTY_AUTOCOMMIT

      Use this connection property to change the default value of autoCommit.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_AUTOCOMMIT_DEFAULT

          static final String CONNECTION_PROPERTY_AUTOCOMMIT_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_AUTOCOMMIT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_AUTOCOMMIT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_PROTOCOL

          static final String CONNECTION_PROPERTY_PROTOCOL

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_PROTOCOL_DEFAULT

          static final String CONNECTION_PROPERTY_PROTOCOL_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_PROTOCOL_ACCESSMODE

          static final byte CONNECTION_PROPERTY_PROTOCOL_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_STREAM_CHUNK_SIZE

          static final String CONNECTION_PROPERTY_STREAM_CHUNK_SIZE

      Deprecated. 
      Stream chunk size for input streams. This property is deprecated since 12.1 and is no longer used internally.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_STREAM_CHUNK_SIZE_DEFAULT

          static final String CONNECTION_PROPERTY_STREAM_CHUNK_SIZE_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_STREAM_CHUNK_SIZE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_STREAM_CHUNK_SIZE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_SET_FLOAT_AND_DOUBLE_USE_BINARY

          static final String CONNECTION_PROPERTY_SET_FLOAT_AND_DOUBLE_USE_BINARY

      If the value of this property is "true", the JDBC PreparedStatement setFloat and setDouble API's convert float and double values to the internal binary format for BINARY_FLOAT or BINARY_DOUBLE before sending to the database. If the property is not set or set to other than "true", the setFloat and setDouble API's convert float and double values to the internal format for NUMBER. See the JavaDoc for setBinaryFloat in oracle.jdbc.PreparedStatement. Use only for 10g or later databases.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_SET_FLOAT_AND_DOUBLE_USE_BINARY_DEFAULT

          static final String CONNECTION_PROPERTY_SET_FLOAT_AND_DOUBLE_USE_BINARY_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_SET_FLOAT_AND_DOUBLE_USE_BINARY_ACCESSMODE

          static final byte CONNECTION_PROPERTY_SET_FLOAT_AND_DOUBLE_USE_BINARY_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_TERMINAL

          static final String CONNECTION_PROPERTY_THIN_VSESSION_TERMINAL

      Use this connection property to change the value that will show up in the "terminal" column of the "v\$session" table for this connection. Note that this setting only applies to the thin driver.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_TERMINAL_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_VSESSION_TERMINAL_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_TERMINAL_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_VSESSION_TERMINAL_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_MACHINE

          static final String CONNECTION_PROPERTY_THIN_VSESSION_MACHINE

      Use this connection property to change the value that will show up in the "machine" column of the "v\$session" table for this connection. Note that this setting only applies to the thin driver.
      If you don't specify a value, by default, the driver will attempt to retrieve your host name. If the attempt fails, it will use "jdbcclient".

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_MACHINE_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_VSESSION_MACHINE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_MACHINE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_VSESSION_MACHINE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_OSUSER

          static final String CONNECTION_PROPERTY_THIN_VSESSION_OSUSER

      By default, the driver retrieves the OS username from the "user.name" system property which is set by the JVM. You can however override this value by using this connection property (thin driver only).
      The OS username will show up in the "osuser" column of the "v\$session" table for this connection.

      If you don't specify any value and if the JVM's "user.name" system property is null, the value will be set to "jdbcuser".

      New in 11gR1: the OS username is also used for OS authentication. This connection property can be used to specify the OS username in cases where the driver can't retrieve it from the JVM. For example if you create the following user in the database:

              > CREATE USER OPS$JDELAVAR IDENTIFIED EXTERNALLY;
              > GRANT CONNECT,RESOURCE,CREATE SESSION TO OPS$JDELAVAR;


      Then you will be able to connect as "OPS\$JDELAVAR" with the following code:
              String url = "jdbc:oracle:thin:@(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=hostname)(PORT=1521))(CONNECT_DATA=(SERVICE_NAME=service)))";
              DriverManager.registerDriver(new oracle.jdbc.OracleDriver());
              Properties props = new Properties();
              props.addProperty(OracleConnection.CONNECTION_PROPERTY_THIN_VSESSION_OSUSER,"jdelavar");
              Connection conn = DriverManager.getConnection(url, props);


      Note that no password was provided because OS authentication is used; in other words, the database server assumes that the client's OS has authenticated the user which is a very naive assumption. Thus and for obvious security reasons, by default, remote OS authentication is disabled in the server. You need to add the following setting in your init.ora file in order to activate it:
      `REMOTE_OS_AUTHENT = TRUE`
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_OSUSER_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_VSESSION_OSUSER_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_OSUSER_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_VSESSION_OSUSER_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_PROGRAM

          static final String CONNECTION_PROPERTY_THIN_VSESSION_PROGRAM

      Use this connection property to change the value that will show up in the "program" column of the "v\$session" table for this connection. Note that this setting only applies to the thin driver.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_PROGRAM_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_VSESSION_PROGRAM_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_PROGRAM_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_VSESSION_PROGRAM_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_PROCESS

          static final String CONNECTION_PROPERTY_THIN_VSESSION_PROCESS

      Use this connection property to change the value that will show up in the "process" column of the "v\$session" table for this connection. Note that this setting only applies to the thin driver.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_PROCESS_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_VSESSION_PROCESS_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_PROCESS_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_VSESSION_PROCESS_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_INAME

          static final String CONNECTION_PROPERTY_THIN_VSESSION_INAME

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_INAME_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_VSESSION_INAME_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_INAME_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_VSESSION_INAME_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_ENAME

          static final String CONNECTION_PROPERTY_THIN_VSESSION_ENAME

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_ENAME_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_VSESSION_ENAME_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_VSESSION_ENAME_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_VSESSION_ENAME_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_PROFILE

          static final String CONNECTION_PROPERTY_THIN_NET_PROFILE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_PROFILE_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_PROFILE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_PROFILE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_PROFILE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_SERVICES

          static final String CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_SERVICES

      Use this connection property to turn on the authentication adaptors. The adaptors are "RADIUS", "KERBEROS" or "TCPS" which is SSL authentication.
      For example, to turn on KERBEROS authentication:

              Properties prop = new Properties();
              prop.setProperty(OracleConnection.CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_SERVICES,
                               "( KERBEROS )");
              prop.setProperty(OracleConnection.CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_MUTUAL,
                               "true");
              // Specify where my krb5 configuration file is because JSSE can't find it:
              System.setProperty("java.security.krb5.conf","C:\\WINDOWS\\krb5.ini");


      Or to turn on RADIUS:

              prop.setProperty(OracleConnection.CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_SERVICES,
                               "( RADIUS)");


      Or to turn on RADIUS, KERBEROS and SSL authentication adaptors:
              prop.setProperty(OracleConnection.CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_SERVICES,
                               "( RADIUS, KERBEROS, SSL)");


      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_SERVICES_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_SERVICES_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_SERVICES_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_SERVICES_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_MUTUAL

          static final String CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_MUTUAL

      To turn on Kerberos mutual authentication, set this property to "true".
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_MUTUAL_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_MUTUAL_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_MUTUAL_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_MUTUAL_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_CC_NAME

          static final String CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_CC_NAME

      Use this connection property to specify the location of the Kerberos credential cache.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_CC_NAME_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_CC_NAME_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_CC_NAME_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_CC_NAME_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_REALM

          static final String CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_REALM

      Use this connection property to specify the realm used for Kerberos authentication.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_REALM_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_REALM_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_REALM_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_REALM_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_JAAS_LOGIN_MODULE

          static final String CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_JAAS_LOGIN_MODULE

      Use this connection property to specify the name of the `JAAS` login module which will be used for initializing `javax.security.auth.login.LoginContext`. This property works in conjunction with the JAAS configuration. Please refer JDK documentation to know about configuring the JAAS config file. By default the Thin driver uses `com.sun.security.auth.module.Krb5LoginModule` as LoginModule and the Kerberos Credential Cache configured via `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_CC_NAME` is used for retreiving the TGT. The default value is `null`. The JAAS configuration is used only if this property is configured with login module name.
      See Also:
      `CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB5_CC_NAME`, `//_end_m4_ifInServer`, [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_JAAS_LOGIN_MODULE_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_JAAS_LOGIN_MODULE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_JAAS_LOGIN_MODULE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_AUTHENTICATION_KRB_JAAS_LOGIN_MODULE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_LEVEL

          static final String CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_LEVEL

      Use this property to specify the level of security for the encryption service. In order of increasing security the parameter can be (note that the default is "ACCEPTED"):\<bt\>
      - "REJECTED": Select this value if you do not elect to enable the encryption service, even if required by the other side. In this scenario, this side of the connection specifies that the encryption service is not permitted. If the other side is set to REQUIRED, the connection terminates with error message ORA-12650. If the other side is set to REQUESTED, ACCEPTED, or REJECTED, the connection continues without error and without the encryption service enabled.
      - "ACCEPTED": Select this value to enable the encryption service if required or requested by the other side. In this scenario, this side of the connection does not require the encryption service, but it is enabled if the other side is set to REQUIRED or REQUESTED. If the other side is set to REQUIRED or REQUESTED, and an encryption algorithm match is found, the connection continues without error and with the encryption service enabled. If the other side is set to REQUIRED and no algorithm match is found, the connection terminates with error message ORA-12650. If the other side is set to REQUESTED and no algorithm match is found, or if the other side is set to ACCEPTED or REJECTED, the connection continues without error and without the security service enabled.
      - "REQUESTED": Select this value to enable the encryption service if the other side permits it. In this scenario, this side of the connection specifies that the security service is desired but not required. The security service is enabled if the other side specifies ACCEPTED, REQUESTED, or REQUIRED. There must be a matching algorithm available on the other side--otherwise the service is not enabled. If the other side specifies REQUIRED and there is no matching algorithm, the connection fails.
      - "REQUIRED": Select this value to enable the encryption service or preclude the connection. In this scenario, this side of the connection specifies that the encryption service must be enabled. The connection fails if the other side specifies REJECTED or if there is no compatible algorithm on the other side.

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_LEVEL_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_LEVEL_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_LEVEL_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_LEVEL_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_TYPES

          static final String CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_TYPES

      Use this connection property to specify the list of encryption algorithms that you want to activate.
      The supported algorithms are:

      - "AES256": AES 256-bit key
      - "AES192": AES 192-bit key
      - "AES128": AES 128-bit key
      - "3DES168": 3-key 3DES
      - "3DES112": 2-key 3DES
      - "DES56C": DES 56-bit key CBC
      - "DES40C": DES 40-bit key CBC
      - "RC4_256": RC4 256-bit key
      - "RC4_128": RC4 128-bit key
      - "RC4_56": RC4 56-bit key
      - "RC4_40": RC4 40-bit key

      For example, if you require the connection to be encrypted with either AES256 or AES192, you would set the following properties:

              prop.setProperty(OracleConnection.CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_TYPES,
                               "( AES256, AES192 )");
              prop.setProperty(OracleConnection.CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_LEVEL,
                               "REQUIRED");


      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_TYPES_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_TYPES_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_TYPES_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_TYPES_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_CHECKSUM_LEVEL

          static final String CONNECTION_PROPERTY_THIN_NET_CHECKSUM_LEVEL

      Use this property to specify the level of security for the integrity service.
      See javadoc for CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_LEVEL.

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_CHECKSUM_LEVEL_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_CHECKSUM_LEVEL_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_CHECKSUM_LEVEL_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_CHECKSUM_LEVEL_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_CHECKSUM_TYPES

          static final String CONNECTION_PROPERTY_THIN_NET_CHECKSUM_TYPES

      Use this connection property to specify the list of integrity algorithms that you want to activate.
      The supported algorithms are:

      - "MD5"

      - "SHA1"

      - "SHA256"

      - "SHA384"

      - "SHA512"

      -

      <!-- -->

              prop.setProperty(OracleConnection.CONNECTION_PROPERTY_THIN_NET_CHECKSUM_TYPES,
                               "( MD5, SHA1, SHA256, SHA384 or SHA512 )");
              prop.setProperty(OracleConnection.CONNECTION_PROPERTY_THIN_NET_CHECKSUM_LEVEL,
                               "REQUIRED");


      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_CHECKSUM_TYPES_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_CHECKSUM_TYPES_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_CHECKSUM_TYPES_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_CHECKSUM_TYPES_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_CRYPTO_SEED

          static final String CONNECTION_PROPERTY_THIN_NET_CRYPTO_SEED

      Use this connection property to specify the encryption seed (between 10 and 70 random characters). The encryption seed for the client should not be the same as that for the server. Note that you don't have to specify a seed on the client.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_CRYPTO_SEED_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_CRYPTO_SEED_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_CRYPTO_SEED_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_CRYPTO_SEED_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_USE_JCE_API

          static final String CONNECTION_PROPERTY_THIN_USE_JCE_API

      If the value of this property is `"true"` and Data Encryption service is enabled, then JDK Crypto(JCE) APIs are used for encryption and decryption of the data between the JDBC client and the Oracle Server, otherwise the built-in crypto implementation is used. Since 19.1, the default value is `true` for the Thin driver. If the JVM version is older than 1.8.0_u151, then you need to change the JVM security policy to allow unlimited key sizes. This is done by downloading and replacing the files found in `$JAVA_HOME/lib/security` (`local_policy.jar` and `US_export_policy.jar`). Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files can be downloaded from Oracle website. Since the OJVM does not support the Unlimited Crypto Strength, the default value for the ThinServer is `false`.
      When this property value is set to `"true"` and the Unlimited Crypto Strength is not available then the Thin driver will automatically change this property value to `"false"` and will use the built-in crypto implementation.
      See Also:
      `CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_TYPES`, `CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_LEVEL`, `CONNECTION_PROPERTY_THIN_NET_CHECKSUM_TYPES`, `CONNECTION_PROPERTY_THIN_NET_CHECKSUM_LEVEL`, [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_USE_JCE_API_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_USE_JCE_API_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_USE_JCE_API_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_USE_JCE_API_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_TCP_NO_DELAY

          static final String CONNECTION_PROPERTY_THIN_TCP_NO_DELAY

      If the value of this property is "true", the TCP_NODELAY property is set on the socket when using the Thin driver. See java.net.SocketOptions.TCP_NODELAY. Can be either a system property or a connection property
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_TCP_NO_DELAY_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_TCP_NO_DELAY_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_TCP_NO_DELAY_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_TCP_NO_DELAY_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_READ_TIMEOUT

          static final String CONNECTION_PROPERTY_THIN_READ_TIMEOUT

      Read timeout while reading from the socket. This affects only the thin driver. The value is in milliseconds. Starting from 12.2 this timeout value is set right after the socket establishment and this read timeout will be applicable to the initial NS Protocol negotiation as well. Since 18.1 this value can be followed by 'ms', 'sec' or 'min' (case not sensitive) to indicate 'milliseconds', 'seconds' or 'minutes'.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_READ_TIMEOUT_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_READ_TIMEOUT_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_READ_TIMEOUT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_READ_TIMEOUT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_OUTBOUND_CONNECT_TIMEOUT

          static final String CONNECTION_PROPERTY_THIN_OUTBOUND_CONNECT_TIMEOUT

      The outbound connect timeout controls the time allowed to connect the socket, let the server accept the connection to the desired service, negotiate the NS protocol as well as complete the ASO negotiation. It doesn't include the user authentication.
      This value is in seconds.
      Default value is `"0"` (no timeout).
      This affects only the thin driver.
      This property can also be set through connection URL. The outbound timeout value set in the connection URL overrides the value set using connection properties. Since 18.1 this value can be followed by 'ms', 'sec' or 'min' (case not sensitive) to indicate 'milliseconds', 'seconds' or 'minutes'. Here is an example of how to set the outbound connect timeout to 10 seconds through the URL:
      `jdbc:oracle:thin:@(DESCRIPTION=(CONNECT_TIMEOUT=10)`
      `(ADDRESS_LIST=(ADDRESS=(HOST=myhost)(PORT=5521)(PROTOCOL=tcp)))(CONNECT_DATA=(SERVICE_NAME=myService)))`
      Since:
      12.2

      See Also:
      `CONNECTION_PROPERTY_THIN_NET_CONNECT_TIMEOUT`, [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_OUTBOUND_CONNECT_TIMEOUT_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_OUTBOUND_CONNECT_TIMEOUT_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_OUTBOUND_CONNECT_TIMEOUT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_OUTBOUND_CONNECT_TIMEOUT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_CONNECT_TIMEOUT

          static final String CONNECTION_PROPERTY_THIN_NET_CONNECT_TIMEOUT

      The connect timeout controls how much time is allowed to connect the socket to the database. Successfully connecting the socket doesn't necessarily mean that the database service is up but it means that the listener is accepting connections.
      This value is in seconds.
      Default value is `"0"` (no timeout). This affects only the thin driver. The connect timeout can also be set through the connection URL using TRANSPORT_CONNECT_TIMEOUT like in the example below. The value set in the URL overrides the value set in this property.
      Since 18.1 this value can be followed by 'ms', 'sec' or 'min' (case not sensitive) to indicate 'milliseconds', 'seconds' or 'minutes'.
      Here is an example of how to set the connect timeout to 5 seconds through the URL:
      `jdbc:oracle:thin:@(DESCRIPTION=(TRANSPORT_CONNECT_TIMEOUT=5)`
      `(ADDRESS_LIST=(ADDRESS=(HOST=myhost)(PORT=5521)(PROTOCOL=tcp)))(CONNECT_DATA=(SERVICE_NAME=myService)))`
      See Also:
      `CONNECTION_PROPERTY_THIN_OUTBOUND_CONNECT_TIMEOUT`, [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_CONNECT_TIMEOUT_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_CONNECT_TIMEOUT_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_CONNECT_TIMEOUT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_CONNECT_TIMEOUT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_DISABLE_OUT_OF_BAND_BREAK

          static final String CONNECTION_PROPERTY_THIN_NET_DISABLE_OUT_OF_BAND_BREAK

      Thin uses out of band breaks by default from 11g onwards. If the user prefers to use Inband breaks instead of Out of Band ones then this property could be set to true.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_DISABLE_OUT_OF_BAND_BREAK_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_DISABLE_OUT_OF_BAND_BREAK_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_DISABLE_OUT_OF_BAND_BREAK_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_DISABLE_OUT_OF_BAND_BREAK_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_USE_ZERO_COPY_IO

          static final String CONNECTION_PROPERTY_THIN_NET_USE_ZERO_COPY_IO

      The thin driver uses the zero-copy IO codepath for SecureFile Lobs by default from 11gR2 onwards. To use the regular codepath, set this property to "false".
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_USE_ZERO_COPY_IO_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_USE_ZERO_COPY_IO_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_USE_ZERO_COPY_IO_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_USE_ZERO_COPY_IO_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_USE_1900_AS_YEAR_FOR_TIME

          static final String CONNECTION_PROPERTY_USE_1900_AS_YEAR_FOR_TIME

      setTime used to set the date component to 01 Jan, 1900 by default in earlier versions (version \< 10g). However, this changed after 10.1 where the time date component in the time was also honored by Jdbc. This flag is introduced to retain the old behavior (as in 9.2)
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_USE_1900_AS_YEAR_FOR_TIME_DEFAULT

          static final String CONNECTION_PROPERTY_USE_1900_AS_YEAR_FOR_TIME_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_USE_1900_AS_YEAR_FOR_TIME_ACCESSMODE

          static final byte CONNECTION_PROPERTY_USE_1900_AS_YEAR_FOR_TIME_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_TIMESTAMPTZ_IN_GMT

          static final String CONNECTION_PROPERTY_TIMESTAMPTZ_IN_GMT

      Obtain TIMESTAMP WITH TIME ZONE value in GMT than adjusting the same to local time zone. default is true.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_TIMESTAMPTZ_IN_GMT_DEFAULT

          static final String CONNECTION_PROPERTY_TIMESTAMPTZ_IN_GMT_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_TIMESTAMPTZ_IN_GMT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_TIMESTAMPTZ_IN_GMT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_TIMEZONE_AS_REGION

          static final String CONNECTION_PROPERTY_TIMEZONE_AS_REGION

      Use JVM default timezone as specified rather than convert to a GMT offset. Default is true.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_TIMEZONE_AS_REGION_DEFAULT

          static final String CONNECTION_PROPERTY_TIMEZONE_AS_REGION_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_TIMEZONE_AS_REGION_ACCESSMODE

          static final byte CONNECTION_PROPERTY_TIMEZONE_AS_REGION_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_CERTIFICATE_ALIAS

          static final String CONNECTION_PROPERTY_THIN_SSL_CERTIFICATE_ALIAS

      When a keystore (either wallet or jks file) contains multiple certificates, this property can be used to specify the alias name of the certificate to be used by the driver during the client authentication part of the SSL handshake.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_CERTIFICATE_ALIAS_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_SSL_CERTIFICATE_ALIAS_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_CERTIFICATE_ALIAS_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_SSL_CERTIFICATE_ALIAS_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_SERVER_DN_MATCH

          static final String CONNECTION_PROPERTY_THIN_SSL_SERVER_DN_MATCH

      Use this connection property to enable or disable the authentication of the server during the SSL handshake. Authenticating the server means that the driver will verify that the Distinguished Name (DN) of the server's certificate matches the one that's specified either in the connection string using "ssl_server_cert_dn" or through the connection property "oracle.net.ssl_server_cert_dn". Starting in 18.0, the driver will automatically authenticate the server if its DN is specified. You can use this property to disable authentication by setting the value to "false".
      See Also:
      `CONNECTION_PROPERTY_THIN_SSL_SERVER_CERT_DN`, [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_SERVER_DN_MATCH_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_SSL_SERVER_DN_MATCH_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_SERVER_DN_MATCH_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_SSL_SERVER_DN_MATCH_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_SERVER_CERT_DN

          static final String CONNECTION_PROPERTY_THIN_SSL_SERVER_CERT_DN

      Use this connection property to specify the distinguished name (DN) of the server used during the SSL handshake to authenticate the server. This value can also be configured in the URL using the parameter "ssl_server_cert_dn". The value set in the URL overrides the value set in this property.
      Since:
      18.0

      See Also:
      `CONNECTION_PROPERTY_THIN_SSL_SERVER_DN_MATCH`, [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_SERVER_CERT_DN_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_SSL_SERVER_CERT_DN_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_SERVER_CERT_DN_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_SSL_SERVER_CERT_DN_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_VERSION

          static final String CONNECTION_PROPERTY_THIN_SSL_VERSION

      Sets the SSL version which will be used for SSL protocol negotiation.
      This is an optional property. By default the JDBC thin driver uses all the protocols supported by JVM out of which SSLv3 and SSLv2Hello are excluded since they are not supported by the Oracle Database starting in 12.2.
      Following are the valid values and the corresponding protocol versions used during negotiation.
      `"0"` - TLSv1.0 or TLSv1.1 or TLSv1.2
      `"undetermined"` - TLSv1.0 or TLSv1.1 or TLSv1.2
      `"2"` - SSLv2Hello
      `"2.0"` - SSLv2Hello
      `"version 2"` - SSLv2Hello
      `"3"` - SSLv3
      `"3.0"` - SSLv3
      `"version 3 only"` - SSLv3
      `"1"` - TLSv1.0
      `"1.0"` - TLSv1.0
      `"version 1 only"` - TLSv1.0
      `"1 or 3"` - TLSv1.0 or SSLv3
      `"1.0 or 3.0"` - TLSv1.0 or SSLv3
      `"version 1 or version 3"` - TLSv1.0 or SSLv3
      `"1.1"` - TLSv1.1
      `"1.2"` - TLSv1.2
      `"1.1 or 3.0"` - TLSv1.1 or SSLv3
      `"1.2 or 3.0"` - TLSv1.2 or SSLv3
      `"1.1 or 1.0"` - TLSv1.1 or TLSv1.0
      `"1.2 or 1.0"` - TLSv1.2 or TLSv1.0
      `"1.2 or 1.1"` - TLSv1.2 or TLSv1.1
      `"1.1 or 1.0 or 3.0"` - TLSv1.1 or TLSv1.0 or SSLv3
      `"1.2 or 1.0 or 3.0"` - TLSv1.2 or TLSv1.0 or SSLv3
      `"1.2 or 1.1 or 1.0"` - TLSv1.2 or TLSv1.1 or TLSv1.0
      `"1.2 or 1.1 or 3.0"` - TLSv1.2 or TLSv1.1 or SSLv3
      `"1.2 or 1.1 or 1.0 or 3.0"` - TLSv1.2 or TLSv1.1 or TLSv1.0 or SSLv3
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_VERSION_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_SSL_VERSION_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_VERSION_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_SSL_VERSION_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_CIPHER_SUITES

          static final String CONNECTION_PROPERTY_THIN_SSL_CIPHER_SUITES

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_CIPHER_SUITES_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_SSL_CIPHER_SUITES_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_CIPHER_SUITES_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_SSL_CIPHER_SUITES_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORE

          static final String CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORE_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORETYPE

          static final String CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORETYPE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORETYPE_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORETYPE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORETYPE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTORETYPE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTOREPASSWORD

          static final String CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTOREPASSWORD

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTOREPASSWORD_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTOREPASSWORD_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTOREPASSWORD_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_KEYSTOREPASSWORD_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORE

          static final String CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORE_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORETYPE

          static final String CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORETYPE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORETYPE_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORETYPE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORETYPE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORETYPE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTOREPASSWORD

          static final String CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTOREPASSWORD

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTOREPASSWORD_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTOREPASSWORD_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTOREPASSWORD_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTOREPASSWORD_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_KEYMANAGERFACTORY_ALGORITHM

          static final String CONNECTION_PROPERTY_THIN_SSL_KEYMANAGERFACTORY_ALGORITHM

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_KEYMANAGERFACTORY_ALGORITHM_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_SSL_KEYMANAGERFACTORY_ALGORITHM_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_KEYMANAGERFACTORY_ALGORITHM_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_SSL_KEYMANAGERFACTORY_ALGORITHM_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_TRUSTMANAGERFACTORY_ALGORITHM

          static final String CONNECTION_PROPERTY_THIN_SSL_TRUSTMANAGERFACTORY_ALGORITHM

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_TRUSTMANAGERFACTORY_ALGORITHM_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_SSL_TRUSTMANAGERFACTORY_ALGORITHM_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_SSL_TRUSTMANAGERFACTORY_ALGORITHM_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_SSL_TRUSTMANAGERFACTORY_ALGORITHM_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_OLDSYNTAX

          static final String CONNECTION_PROPERTY_THIN_NET_OLDSYNTAX

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_OLDSYNTAX_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_OLDSYNTAX_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_OLDSYNTAX_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_OLDSYNTAX_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JNDI_LDAP_CONNECT_TIMEOUT

          static final String CONNECTION_PROPERTY_THIN_JNDI_LDAP_CONNECT_TIMEOUT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JNDI_LDAP_CONNECT_TIMEOUT_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_JNDI_LDAP_CONNECT_TIMEOUT_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JNDI_LDAP_CONNECT_TIMEOUT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_JNDI_LDAP_CONNECT_TIMEOUT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JNDI_LDAP_READ_TIMEOUT

          static final String CONNECTION_PROPERTY_THIN_JNDI_LDAP_READ_TIMEOUT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JNDI_LDAP_READ_TIMEOUT_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_JNDI_LDAP_READ_TIMEOUT_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_JNDI_LDAP_READ_TIMEOUT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_JNDI_LDAP_READ_TIMEOUT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_WALLET_LOCATION

          static final String CONNECTION_PROPERTY_WALLET_LOCATION

      Use this property to specify the wallet location. The driver will use this wallet to:
      - Retrieve the username and password which can be stored in a wallet. The driver attempts to retrieve the username and password from the wallet unless they are specified in the JDBC URL or in the properties (in order, it will look in the properties first, then in the URL and then in the wallet). The "mkstore" utility can be used to store the username and password in an existing wallet. For example, if the wallet is in the "client_wallet" directory: `mkstore -wrl ./client_wallet -createCredential \(DESCRIPTION=\(ADDRESS=\(PROTOCOL=tcp\)\(HOST=servername\)\( PORT=5560\)\)\(CONNECT_DATA=\(SERVICE_NAME=service_name\)\)\) scott tiger`
      - Create an SSL connection if the TCPS protocol is enabled. The wallet is used for both the truststore and the keystore and overwrites the JSSE properties.

      The wallet location can be set in two formats:

      - `file:/path/ewallet.sso" or "file:/path/cwallet.p12" or "file:/path/to/directory/`
      - `(SOURCE=(METHOD=FILE)(METHOD_DATA=(DIRECTORY=/path/to/directory)))`

      Note that if you don't use SSO wallets but PKCS12 wallets, you must provide the wallet password through the "oracle.net.wallet_password" property.

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_WALLET_LOCATION_DEFAULT

          static final String CONNECTION_PROPERTY_WALLET_LOCATION_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_WALLET_LOCATION_ACCESSMODE

          static final byte CONNECTION_PROPERTY_WALLET_LOCATION_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_WALLET_PASSWORD

          static final String CONNECTION_PROPERTY_WALLET_PASSWORD

      Use this property to set the wallet password which is only required if you don't enable enable auto-login in the wallet. In this case "ewallet.p12" will be used instead of "cwallet.sso".
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_WALLET_PASSWORD_DEFAULT

          static final String CONNECTION_PROPERTY_WALLET_PASSWORD_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_WALLET_PASSWORD_ACCESSMODE

          static final byte CONNECTION_PROPERTY_WALLET_PASSWORD_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_CIPHER_SUITES

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_CIPHER_SUITES

      Use this property to specify the valid cipher suites used while SSL negotiation with LDAP server. Multiple cipher suite names can be seperated by comma. The default value is `null`.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_CIPHER_SUITES_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_CIPHER_SUITES_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_CIPHER_SUITES_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_LDAP_SSL_CIPHER_SUITES_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_VERSIONS

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_VERSIONS

      Use this property to specify the valid SSL protocol version(s) used while SSL negotiation with LDAP Server. Multiple protocol versions can be seperated by comma. The default value is `null`. The valid protocol versions are
      `TLSv1.2`
      `TLSv1.1`
      `TLSv1`
      `SSLv3`
      `SSLv2Hello`
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_VERSIONS_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_VERSIONS_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_VERSIONS_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_LDAP_SSL_VERSIONS_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_TYPE

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_TYPE

      This property is used to specify the type of the KeyStore file which will be used while SSL negotiation with LDAP server. The default value is `null`.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_TYPE_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_TYPE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_TYPE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_TYPE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE

      This property is used to specify the KeyStore file path which will be used while SSL negotiation with LDAP server. The default value is `null`. When no value is specified, the default keystore of the runtime is used.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_PASSWORD

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_PASSWORD

      This property is used to specify the password for the KeyStore file which will be used while SSL negotiation with LDAP server. The default value is `null`.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_PASSWORD_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_PASSWORD_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_PASSWORD_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYSTORE_PASSWORD_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYMANAGER_FACTORY_ALGORITHM

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYMANAGER_FACTORY_ALGORITHM

      Use this property to override the default algorithm used by KeyManagerFactory. The default value is `null`.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYMANAGER_FACTORY_ALGORITHM_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYMANAGER_FACTORY_ALGORITHM_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYMANAGER_FACTORY_ALGORITHM_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_LDAP_SSL_KEYMANAGER_FACTORY_ALGORITHM_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_TYPE

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_TYPE

      This property is used to specify the type of the TrustStore file which will be used while SSL negotiation with LDAP server. The default value is `null`.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_TYPE_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_TYPE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_TYPE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_TYPE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE

      This property is used to specify the TrustStore file path which will be used while SSL negotiation with LDAP server. The default value is `null`. When no value is specified, the default truststore of the runtime is used.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_PASSWORD

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_PASSWORD

      This property is used to specify the password for the TrustStore file which will be used while SSL negotiation with LDAP server. The default value is `null`.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_PASSWORD_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_PASSWORD_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_PASSWORD_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTSTORE_PASSWORD_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTMANAGER_FACTORY_ALGORITHM

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTMANAGER_FACTORY_ALGORITHM

      Use this property to override the default algorithm used by TrustManagerFactory. The default value is `null`.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTMANAGER_FACTORY_ALGORITHM_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTMANAGER_FACTORY_ALGORITHM_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTMANAGER_FACTORY_ALGORITHM_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_LDAP_SSL_TRUSTMANAGER_FACTORY_ALGORITHM_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_LOCATION

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_LOCATION

      Use this property to specify the wallet location. The driver will use this wallet while SSL negotiation with LDAP server. The default value is `null`.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_LOCATION_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_LOCATION_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_LOCATION_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_LOCATION_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_PASSWORD

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_PASSWORD

      Use this property to specify the password of the wallet file which will be used while SSL negotiation with LDAP server. The default value is `null`.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_PASSWORD_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_PASSWORD_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_PASSWORD_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_LDAP_SSL_WALLET_PASSWORD_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_PROXY_CLIENT_NAME

          static final String CONNECTION_PROPERTY_PROXY_CLIENT_NAME

      The value of this property is used to specify the name of the proxy client during proxy authentication.
      For example if a database user "proxyclient" is setup to connect through another user called "proxy", then you would set the value of this property to "proxyclient".

      Note that this connection property can be used to obtain a proxy client connection from scratch and in this model there is only one database session involved instead of two when you first create a regular connection as "proxy" and then call `openProxySession(...)` to obtain a proxy client session. This is called the single-session proxy model. This property is only supported for connections to database versions of 10.2 and higher. There is no support for the single-session proxy model in earlier database versions.

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_PROXY_CLIENT_NAME_DEFAULT

          static final String CONNECTION_PROPERTY_PROXY_CLIENT_NAME_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_PROXY_CLIENT_NAME_ACCESSMODE

          static final byte CONNECTION_PROPERTY_PROXY_CLIENT_NAME_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULT_USE_NIO

          static final String CONNECTION_PROPERTY_DEFAULT_USE_NIO

      In case of Jdbc-OCI drivers the data is copied from C layer to Java using Jni array copy api. Alternatively by setting this property to "true" the user can instruct the driver to copy data using NIO. Note that the feature would enabled if the underlying JVM supports NIO in JNI layer. The flag is turned off by default (set to false).
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULT_USE_NIO_DEFAULT

          static final String CONNECTION_PROPERTY_DEFAULT_USE_NIO_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULT_USE_NIO_ACCESSMODE

          static final byte CONNECTION_PROPERTY_DEFAULT_USE_NIO_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_DRIVER_CHARSET

          static final String CONNECTION_PROPERTY_OCI_DRIVER_CHARSET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_DRIVER_CHARSET_DEFAULT

          static final String CONNECTION_PROPERTY_OCI_DRIVER_CHARSET_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_DRIVER_CHARSET_ACCESSMODE

          static final byte CONNECTION_PROPERTY_OCI_DRIVER_CHARSET_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_EDITION_NAME

          static final String CONNECTION_PROPERTY_EDITION_NAME

      This connection property can be used to specify a name for the "session edition". The value is sent to the server at connection time.
      The following SQL query:

          SELECT sys_context('USERENV', 'CURRENT_EDITION_NAME')
              FROM dual

      will return the same value.
      Note that this property can also be set as a system property.

      By default, if you don't set this property, the "session edition" will be set to the database default edition (for example "ORA\$BASE").

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_EDITION_NAME_DEFAULT

          static final String CONNECTION_PROPERTY_EDITION_NAME_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_EDITION_NAME_ACCESSMODE

          static final byte CONNECTION_PROPERTY_EDITION_NAME_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_INTERNAL_LOGON

          static final String CONNECTION_PROPERTY_INTERNAL_LOGON

      The value of this property is used as the user name when performing an internal logon. Usually this will be "SYS" or "SYSDBA".
      As of 12.1 server and driver, "SYSBACKUP", "SYSDG" and "SYSKM" are also supported.

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_INTERNAL_LOGON_DEFAULT

          static final String CONNECTION_PROPERTY_INTERNAL_LOGON_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_INTERNAL_LOGON_ACCESSMODE

          static final byte CONNECTION_PROPERTY_INTERNAL_LOGON_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_CREATE_DESCRIPTOR_USE_CURRENT_SCHEMA_FOR_SCHEMA_NAME

          static final String CONNECTION_PROPERTY_CREATE_DESCRIPTOR_USE_CURRENT_SCHEMA_FOR_SCHEMA_NAME

      The user has to provide fully qualified ADT name (\[username\].\[adt name\]) for all ADT operations. However, if the user does not provide fully qualified name, the user name provided during login is appended to the ADT name to obtain fully qualified name. This is also the behavior when this flag is set to `false`.
      The user also has an option to append the CURRENT_USER value to the ADT name to obtain fully qualified name by setting this property to `true`. Note that it takes a network round trip to fetch the CURRENT_SCHEMA value.

      The default value of this flag is `false` which means that the driver appends the user name used to login as the user name to append to the ADT name.

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_CREATE_DESCRIPTOR_USE_CURRENT_SCHEMA_FOR_SCHEMA_NAME_DEFAULT

          static final String CONNECTION_PROPERTY_CREATE_DESCRIPTOR_USE_CURRENT_SCHEMA_FOR_SCHEMA_NAME_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_CREATE_DESCRIPTOR_USE_CURRENT_SCHEMA_FOR_SCHEMA_NAME_ACCESSMODE

          static final byte CONNECTION_PROPERTY_CREATE_DESCRIPTOR_USE_CURRENT_SCHEMA_FOR_SCHEMA_NAME_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_SVC_CTX_HANDLE

          static final String CONNECTION_PROPERTY_OCI_SVC_CTX_HANDLE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_SVC_CTX_HANDLE_DEFAULT

          static final String CONNECTION_PROPERTY_OCI_SVC_CTX_HANDLE_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_SVC_CTX_HANDLE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_OCI_SVC_CTX_HANDLE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_ENV_HANDLE

          static final String CONNECTION_PROPERTY_OCI_ENV_HANDLE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_ENV_HANDLE_DEFAULT

          static final String CONNECTION_PROPERTY_OCI_ENV_HANDLE_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_ENV_HANDLE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_OCI_ENV_HANDLE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_ERR_HANDLE

          static final String CONNECTION_PROPERTY_OCI_ERR_HANDLE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_ERR_HANDLE_DEFAULT

          static final String CONNECTION_PROPERTY_OCI_ERR_HANDLE_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_ERR_HANDLE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_OCI_ERR_HANDLE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_PRELIM_AUTH

          static final String CONNECTION_PROPERTY_PRELIM_AUTH

      If this property is set to "true", JDBC drivers connect in PRELIM_AUTH mode, which is the only mode that is permitted when the database is down.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_PRELIM_AUTH_DEFAULT

          static final String CONNECTION_PROPERTY_PRELIM_AUTH_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_PRELIM_AUTH_ACCESSMODE

          static final byte CONNECTION_PROPERTY_PRELIM_AUTH_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_SET_NEW_PASSWORD

          static final String CONNECTION_PROPERTY_SET_NEW_PASSWORD

      Deprecated. 
      Property which sets enables the user to set a new password during connection. This property is deprecated since 12.2 and should not be used. Use oracle.jdbc.newPassword.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_SET_NEW_PASSWORD_DEFAULT

          static final String CONNECTION_PROPERTY_SET_NEW_PASSWORD_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_SET_NEW_PASSWORD_ACCESSMODE

          static final byte CONNECTION_PROPERTY_SET_NEW_PASSWORD_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULT_EXECUTE_BATCH

          static final String CONNECTION_PROPERTY_DEFAULT_EXECUTE_BATCH

      Deprecated. Oracle-Style batching is desupported. Standard JDBC batch execution is recommended instead.
      The value of this property is ignored since the 20c release. Prior to 20c, the value of this property would configure the default batch size when using Oracle-Style batching.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULT_EXECUTE_BATCH_DEFAULT

          static final String CONNECTION_PROPERTY_DEFAULT_EXECUTE_BATCH_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULT_EXECUTE_BATCH_ACCESSMODE

          static final byte CONNECTION_PROPERTY_DEFAULT_EXECUTE_BATCH_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULT_ROW_PREFETCH

          static final String CONNECTION_PROPERTY_DEFAULT_ROW_PREFETCH

      The value of this property is used as the default number of rows to prefetch.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULT_ROW_PREFETCH_DEFAULT

          static final String CONNECTION_PROPERTY_DEFAULT_ROW_PREFETCH_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULT_ROW_PREFETCH_ACCESSMODE

          static final byte CONNECTION_PROPERTY_DEFAULT_ROW_PREFETCH_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULT_LOB_PREFETCH_SIZE

          static final String CONNECTION_PROPERTY_DEFAULT_LOB_PREFETCH_SIZE

      The value of this property is used as the default LOB prefetch size for this connection.
      The LOB prefetch size can be overriden at the statement level through the `setLobPrefetchSize(int)` which is defined in `oracle.jdbc.OracleStatement`. The statement level LOB prefetch size can be overriden at the column level through the `defineColumnType` method.

      The value can be "-1" to disable LOB prefetch for this connection, "0" to enable LOB prefetch for meta-data only or any value greater than 0 which represents a number of bytes for BLOBs and chars for CLOBs to be prefetched along with the locator during fetch operations. The default value for this property is "4000".

      Since:
      11.2

      See Also:
      [`OracleStatement.setLobPrefetchSize`](OracleStatement.md), [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULT_LOB_PREFETCH_SIZE_DEFAULT

          static final String CONNECTION_PROPERTY_DEFAULT_LOB_PREFETCH_SIZE_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULT_LOB_PREFETCH_SIZE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_DEFAULT_LOB_PREFETCH_SIZE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_DATA_IN_LOCATOR

          static final String CONNECTION_PROPERTY_ENABLE_DATA_IN_LOCATOR

      The value of this property is used to control the use of the Data in Locator feature of the server.
      Data in Locator is a server side feature introduced in 10.2. For small lobs the actual data in included in the locator bytes shipped to the client. These may be shipped back and forth several times as the client accesses the lob using the lob APIs. For fast networks this actually increases performance because it greatly reduces server CPU consumption.

      For slower networks there is a net slow down. Setting this property to false will disable this feature.

      This property is currently only effective for the thin driver.

      Data in Locator is automatically disabled when Lob Prefetch is enabled. Thus this property will most likely be used for 10.2 servers where lob prefetch is not available.

      Since:
      11.2

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_DATA_IN_LOCATOR_DEFAULT

          static final String CONNECTION_PROPERTY_ENABLE_DATA_IN_LOCATOR_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_DATA_IN_LOCATOR_ACCESSMODE

          static final byte CONNECTION_PROPERTY_ENABLE_DATA_IN_LOCATOR_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_READ_DATA_IN_LOCATOR

          static final String CONNECTION_PROPERTY_ENABLE_READ_DATA_IN_LOCATOR

      The value of this property is used to control the use of the Data in Locator feature by the client.
      Data in Locator is a server side feature introduced in 10.2. The JDBC driver is enhanced to use this data directly. This saves a number of round trips which previously occurred when lob APIs were used to read the data.

      This feature is only enabled for 10.2 servers. For earlier servers the Data in Locator feature did not exist and for later ones the lob prefetch functionality make this uunnecessary and the new lob storage types complicate the locator structure.

      Since:
      11.2

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_READ_DATA_IN_LOCATOR_DEFAULT

          static final String CONNECTION_PROPERTY_ENABLE_READ_DATA_IN_LOCATOR_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_READ_DATA_IN_LOCATOR_ACCESSMODE

          static final byte CONNECTION_PROPERTY_ENABLE_READ_DATA_IN_LOCATOR_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_REPORT_REMARKS

          static final String CONNECTION_PROPERTY_REPORT_REMARKS

      If the value of this property is "true", OracleDatabaseMetaData will include remarks in the meta data. This can result in a substantial reduction in performance.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_REPORT_REMARKS_DEFAULT

          static final String CONNECTION_PROPERTY_REPORT_REMARKS_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_REPORT_REMARKS_ACCESSMODE

          static final byte CONNECTION_PROPERTY_REPORT_REMARKS_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_INCLUDE_SYNONYMS

          static final String CONNECTION_PROPERTY_INCLUDE_SYNONYMS

      If the value of this property is "true", JDBC will include synonyms when getting information about a column.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_INCLUDE_SYNONYMS_DEFAULT

          static final String CONNECTION_PROPERTY_INCLUDE_SYNONYMS_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_INCLUDE_SYNONYMS_ACCESSMODE

          static final byte CONNECTION_PROPERTY_INCLUDE_SYNONYMS_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_RESTRICT_GETTABLES

          static final String CONNECTION_PROPERTY_RESTRICT_GETTABLES

      If the value of this property is "true", JDBC will return a more refined value for DatabaseMeta.getTables. By default JDBC will return things that are not accessible tables. These can be non-table objects or accessible synonymns for inaccessible tables. If this property is true JDBC will return only accessible tables. This has a substantial performance penalty.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_RESTRICT_GETTABLES_DEFAULT

          static final String CONNECTION_PROPERTY_RESTRICT_GETTABLES_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_RESTRICT_GETTABLES_ACCESSMODE

          static final byte CONNECTION_PROPERTY_RESTRICT_GETTABLES_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ACCUMULATE_BATCH_RESULT

          static final String CONNECTION_PROPERTY_ACCUMULATE_BATCH_RESULT

      When using Oracle style batching, JDBC determines when to flush a batch to the database. If this property is true, then the number of modified rows accumulated across all batches flushed from a single statement. The default is to count each batch separately.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ACCUMULATE_BATCH_RESULT_DEFAULT

          static final String CONNECTION_PROPERTY_ACCUMULATE_BATCH_RESULT_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ACCUMULATE_BATCH_RESULT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_ACCUMULATE_BATCH_RESULT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_USE_FETCH_SIZE_WITH_LONG_COLUMN

          static final String CONNECTION_PROPERTY_USE_FETCH_SIZE_WITH_LONG_COLUMN

      If the value of this property is "true", then JDBC will prefetch rows even though there is a LONG or LONG RAW column in the result. By default JDBC fetches only one row at a time if there are LONG or LONG RAW columns in the result. Setting this property to "true" can improve performance but can also cause SQLExceptions if the results are too big.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_USE_FETCH_SIZE_WITH_LONG_COLUMN_DEFAULT

          static final String CONNECTION_PROPERTY_USE_FETCH_SIZE_WITH_LONG_COLUMN_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_USE_FETCH_SIZE_WITH_LONG_COLUMN_ACCESSMODE

          static final byte CONNECTION_PROPERTY_USE_FETCH_SIZE_WITH_LONG_COLUMN_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_PROCESS_ESCAPES

          static final String CONNECTION_PROPERTY_PROCESS_ESCAPES

      If the value of this property is "false" then the default setting for Statement.setEscapeProccessing is false.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_PROCESS_ESCAPES_DEFAULT

          static final String CONNECTION_PROPERTY_PROCESS_ESCAPES_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_PROCESS_ESCAPES_ACCESSMODE

          static final byte CONNECTION_PROPERTY_PROCESS_ESCAPES_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_FIXED_STRING

          static final String CONNECTION_PROPERTY_FIXED_STRING

      If the value of this property is "true", JDBC will use FIXED CHAR semantic when setObject is called with a String argument. By default JDBC uses VARCHAR semantics. The difference is in blank padding. With the default there is no blank padding so, for example, 'a' does not equal 'a ' in a CHAR(4). If true these two will be equal.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_FIXED_STRING_DEFAULT

          static final String CONNECTION_PROPERTY_FIXED_STRING_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_FIXED_STRING_ACCESSMODE

          static final byte CONNECTION_PROPERTY_FIXED_STRING_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULTNCHAR

          static final String CONNECTION_PROPERTY_DEFAULTNCHAR

      If the value of this property is "true", the default mode for all character data columns will be NCHAR.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULTNCHAR_DEFAULT

          static final String CONNECTION_PROPERTY_DEFAULTNCHAR_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULTNCHAR_ACCESSMODE

          static final byte CONNECTION_PROPERTY_DEFAULTNCHAR_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_RESOURCE_MANAGER_ID

          static final String CONNECTION_PROPERTY_RESOURCE_MANAGER_ID

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_RESOURCE_MANAGER_ID_DEFAULT

          static final String CONNECTION_PROPERTY_RESOURCE_MANAGER_ID_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_RESOURCE_MANAGER_ID_ACCESSMODE

          static final byte CONNECTION_PROPERTY_RESOURCE_MANAGER_ID_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DISABLE_DEFINECOLUMNTYPE

          static final String CONNECTION_PROPERTY_DISABLE_DEFINECOLUMNTYPE

      Disable the method OracleStatement.defineColumnType when equal "true". When this connection property has the value true, the method defineColumnType is has no effect. This is highly recommended when using the Thin driver, especially when the database character set contains four byte characters that expand to two UCS2 surrogate characters, e.g. AL32UTF8. The method defineColumnType provides no performance benefit (or any other benefit) when used with the 10g Thin driver. This property is provided so that you do not have to remove the calls from your code. This is especially valuable if you use the same code with Thin driver and either the OCI or Server Internal driver.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DISABLE_DEFINECOLUMNTYPE_DEFAULT

          static final String CONNECTION_PROPERTY_DISABLE_DEFINECOLUMNTYPE_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DISABLE_DEFINECOLUMNTYPE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_DISABLE_DEFINECOLUMNTYPE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_CONVERT_NCHAR_LITERALS

          static final String CONNECTION_PROPERTY_CONVERT_NCHAR_LITERALS

      Convert NCHAR literals to Unicode literals when equal "true". The default is true.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_CONVERT_NCHAR_LITERALS_DEFAULT

          static final String CONNECTION_PROPERTY_CONVERT_NCHAR_LITERALS_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_CONVERT_NCHAR_LITERALS_ACCESSMODE

          static final byte CONNECTION_PROPERTY_CONVERT_NCHAR_LITERALS_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_AUTO_COMMIT_SPEC_COMPLIANT

          static final String CONNECTION_PROPERTY_AUTO_COMMIT_SPEC_COMPLIANT

      Alters the auto-commit behavior of the driver. By default the driver complies with JDBC specification. User can choose to alter the behavior by changing the value of this flag.
      Oracle JDBC 12.1 drivers comply with JDBC specification 4.1 and will:

      - throw `SQLException` when [`Connection.commit()`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#commit__) or [`Connection.rollback()`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#rollback__) is invoked when auto-commit is `true`.
      - issue an implicit commit of the local transaction when [`Connection.setAutoCommit(boolean)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setAutoCommit_boolean_) is called and the mode is changed from `false` to `true`.

      Because the standard behavior may break existing applications, this flag is provided as a convenience and can be set to `false`. Most applications may never need to set this flag. Users are encouraged to modify their applications to support the specification instead of using this flag.

      Since:
      12.1

      See Also:
      [`Connection.commit()`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#commit__), [`Connection.rollback()`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#rollback__), [`Connection.setAutoCommit(boolean)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setAutoCommit_boolean_), [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_AUTO_COMMIT_SPEC_COMPLIANT_DEFAULT

          static final String CONNECTION_PROPERTY_AUTO_COMMIT_SPEC_COMPLIANT_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_AUTO_COMMIT_SPEC_COMPLIANT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_AUTO_COMMIT_SPEC_COMPLIANT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_JDBC_STANDARD_BEHAVIOR

          static final String CONNECTION_PROPERTY_JDBC_STANDARD_BEHAVIOR

      Ensures the driver is in strict compliance with the JDBC specification. When "false" (the default), previous Oracle specific non-standard deviations from the standard are maintained. When "true", this flag will override the behavior of all other compatibility flags. For complete backwards compatibility with previous drivers which differed from the JDBC standards, you should leave this flag set to "false". If you require compliance with the JDBC standard, then " set to "true"; this ensures ALL non-standard behavior is removed from the driver. Note that backwards compatibility and standards compliance is often contradictory and you can't have both.
      Since:
      12.2

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_JDBC_STANDARD_BEHAVIOR_DEFAULT

          static final String CONNECTION_PROPERTY_JDBC_STANDARD_BEHAVIOR_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_JDBC_STANDARD_BEHAVIOR_ACCESSMODE

          static final byte CONNECTION_PROPERTY_JDBC_STANDARD_BEHAVIOR_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_J2EE13_COMPLIANT

          static final String CONNECTION_PROPERTY_J2EE13_COMPLIANT

      Deprecated. This property could be removed in the future and the default will be `true`. So if this property is used as workaround to turn off compliant behavior, consider changing the application.
      If the value of this property is "true", JDBC uses strict compliance for some edge cases. In general Oracle's JDBC drivers will allow some operations that are not permitted in the strict interpretation of J2EE 1.3. Setting this property to true will cause those cases to throw SQLExceptions. There are some other edge cases where Oracle's JDBC drivers have slightly different behavior than defined in J2EE 1.3. This results from Oracle having defined the behavior prior to the J2EE 1.3 specification and the resultant need for compatibility with existing customer code. Setting this property will result in full J2EE 1.3 compliance at the cost of incompatibility with some customer code. Can be either a system property or a connection property.
      The driver would behave differently in the following way when the property is set.

      - Throws an exception when executeQuery is invoked on a DML
      - Throws an exception when executeUpdate is invoked on a Query
      - MetaData.getScale returns 0 for unconstrained NUMBER column
      - getObject on a NUMBER column with precision 0 and scale unconstrained returns Double
      - ResultSetMetaData.getColumnType on a NUMBER column with precision 0 and scale unconstrained returns FLOAT
      - ResultSetMetaData.getColumnClassName on a NUMBER column with precision 0 and scale unconstrained returns java.lang.Double
      - getObject on a TIMESTAMP column returns an object of type java.sql.Timestamp
      - ResultSetMetaData.getColumnClassName on a TIMESTAMP column returns java.sql.Timestamp

      The property is `false` by default for all drivers while using regular JDBC library. The value of this property is `true` by default in DMS jar file.

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_J2EE13_COMPLIANT_DEFAULT

          static final String CONNECTION_PROPERTY_J2EE13_COMPLIANT_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_J2EE13_COMPLIANT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_J2EE13_COMPLIANT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_MAP_DATE_TO_TIMESTAMP

          static final String CONNECTION_PROPERTY_MAP_DATE_TO_TIMESTAMP

      This connection property lets you define how the driver will map SQL DATE values in the database to Java types. Since Oracle SQL DATE includes a time component and java.sql.Date does not, mapping DATE to java.sql.Date looses information. It is more appropriate to map DATE to java.sql.Timestamp and that is the default behavior.
      The 9i and 10g drivers mistakenly mapped DATE to java.sql.Date by default. Setting this property to false will cause the driver to map SQL DATE to java.util.Date with the corresponding loss of time information in each DATE value. This is for backwards compatibility only.

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_MAP_DATE_TO_TIMESTAMP_DEFAULT

          static final String CONNECTION_PROPERTY_MAP_DATE_TO_TIMESTAMP_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_MAP_DATE_TO_TIMESTAMP_ACCESSMODE

          static final byte CONNECTION_PROPERTY_MAP_DATE_TO_TIMESTAMP_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_USE_THREADLOCAL_BUFFER_CACHE

          static final String CONNECTION_PROPERTY_USE_THREADLOCAL_BUFFER_CACHE

      If true, the statement data buffers are cached on a per thread basis. If false, the data buffers are cached on a per connection basis. These buffers can be quite large. It is important that the number of them be minimized.
      In most cases you should use the per connection cache. However if your app has many more idle connections than active connections at any given moment then using the thread local cache may reduce the total JDBC driver memory footprint. If you are not having a problem with Java heap size, leave this alone.

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_USE_THREADLOCAL_BUFFER_CACHE_DEFAULT

          static final String CONNECTION_PROPERTY_USE_THREADLOCAL_BUFFER_CACHE_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_USE_THREADLOCAL_BUFFER_CACHE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_USE_THREADLOCAL_BUFFER_CACHE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DRIVER_NAME_ATTRIBUTE

          static final String CONNECTION_PROPERTY_DRIVER_NAME_ATTRIBUTE

      The value passed to the server for the OCI_ATTR_DRIVER_NAME. This property is supported with both the OCI and Thin drivers. The attribute aids in diagnosability. In most cases you should not need to set it. The value is limited to a maximum of 8 printable 7-bit ASCII characters. The default value depends on which driver is used. The default value for the THIN driver is "jdbcthin" and the default value for the OCI driver is "jdbcoci".
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DRIVER_NAME_ATTRIBUTE_DEFAULT

          static final String CONNECTION_PROPERTY_DRIVER_NAME_ATTRIBUTE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_DRIVER_NAME_ATTRIBUTE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_DRIVER_NAME_ATTRIBUTE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_MAX_CACHED_BUFFER_SIZE

          static final String CONNECTION_PROPERTY_MAX_CACHED_BUFFER_SIZE

      The log base 2 of the size of the largest internal char or byte data buffer that the driver should cache. The default is 30 which means the largest cached buffer is 1 giga(byte/char). Values greater than 30 are treated as the actual buffer size. Values less than 12 will effectively disable the buffer cache. Rather than setting the value less than 16, you should increase the amount of heap available to your application by setting -Xmx and -Xms.
      The driver uses char and byte buffers to retrieve query results. These buffers can be quite large and are cached. If some queries create particularly large buffers, the driver will attempt to cache those large buffers. This may possibly reduce performance. The The best way to approach this problem is to reduce buffer size of those queries by setting their fetch_size to a smaller value, but if that is impractical, you can set this property to prevent these large buffers from being cached. The appropriate value depends on the heap size, number of connections open, number of statements open at once, and fraction of the heap that can be allocated to JDBC. A reasonable starting point for a middle-tier application server might be 21 (2MB). It bears repating that you are better off setting the fetch size of the problematic statements, if possible.

      See Also:
      `USE_THREAD_LOCAL_BUFFER_CACHE`, [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_MAX_CACHED_BUFFER_SIZE_DEFAULT

          static final String CONNECTION_PROPERTY_MAX_CACHED_BUFFER_SIZE_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_MAX_CACHED_BUFFER_SIZE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_MAX_CACHED_BUFFER_SIZE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_IMPLICIT_STATEMENT_CACHE_SIZE

          static final String CONNECTION_PROPERTY_IMPLICIT_STATEMENT_CACHE_SIZE

      The maximum number of statements that will be stored in this connection's statement cache. The default is 0 which disables the statement cache. If set to a value greater than 0, the implicit statement cache is enabled. Calls to setStatementCacheSize and setImplicitCachingEnabled override this.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_IMPLICIT_STATEMENT_CACHE_SIZE_DEFAULT

          static final String CONNECTION_PROPERTY_IMPLICIT_STATEMENT_CACHE_SIZE_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_IMPLICIT_STATEMENT_CACHE_SIZE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_IMPLICIT_STATEMENT_CACHE_SIZE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_LOB_STREAM_POS_STANDARD_COMPLIANT

          static final String CONNECTION_PROPERTY_LOB_STREAM_POS_STANDARD_COMPLIANT

      Previous releases allowed the value of 0L to be set for the position parameter of Blob.setBinaryStream and Clob.setAsciiStream and setCharacterStream which is not correct in the specification. It had the same effect as setting 1L. This was a legacy of the orginal Oracle proprietary APiS. If this switch is set false the old incorrect behavior is retained for compatibility
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_LOB_STREAM_POS_STANDARD_COMPLIANT_DEFAULT

          static final String CONNECTION_PROPERTY_LOB_STREAM_POS_STANDARD_COMPLIANT_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_LOB_STREAM_POS_STANDARD_COMPLIANT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_LOB_STREAM_POS_STANDARD_COMPLIANT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_STRICT_ASCII_CONVERSION

          static final String CONNECTION_PROPERTY_STRICT_ASCII_CONVERSION

      The Oracle JDBC has been doing quick ASCII conversion (use only the low bytes) in different areas for the sake of performance. However, when the input characters are not pure ASCII, they need to be converted to the corresponding ASCII replacement characters. To accomodate this need, Oracle JDBC implements this flag. This flag is default to false, in which no characters will be converted, quick ASCII conversion is done for good performance. When this flag is set to true, Oracle JDBC will check for non-ASCII characters and convert them with replacement characters. This flag controls all areas where ASCII conversion is done.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_STRICT_ASCII_CONVERSION_DEFAULT

          static final String CONNECTION_PROPERTY_STRICT_ASCII_CONVERSION_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_STRICT_ASCII_CONVERSION_ACCESSMODE

          static final byte CONNECTION_PROPERTY_STRICT_ASCII_CONVERSION_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_CONNECTION_CLASS

          static final String CONNECTION_PROPERTY_CONNECTION_CLASS

      Specify the connection class name for Database Resident Connection Pool (DRCP). Connection class must be provided to enable DRCP. Along with the connection class the URL must be altered to include `(SERVER=POOLED)` in long URL form. In thin the short URL form should be modified to append `:POOLED`.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_CONNECTION_CLASS_DEFAULT

          static final String CONNECTION_PROPERTY_CONNECTION_CLASS_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_CONNECTION_CLASS_ACCESSMODE

          static final byte CONNECTION_PROPERTY_CONNECTION_CLASS_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DRCP_TAG_NAME

          static final String CONNECTION_PROPERTY_DRCP_TAG_NAME

      This is the tag name that for Database Resident Connection Pool (DRCP). Tag name is provided during connect time. The server will make an attempt to obtain a server process of the same tag. If it succeeds the next `#attachConnection()` will return `true`.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DRCP_TAG_NAME_DEFAULT

          static final String CONNECTION_PROPERTY_DRCP_TAG_NAME_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_DRCP_TAG_NAME_ACCESSMODE

          static final byte CONNECTION_PROPERTY_DRCP_TAG_NAME_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_CONNECTION_PURITY

          static final String CONNECTION_PROPERTY_CONNECTION_PURITY

      Specify the connection purity for a Database Resident Connection Pool (DRCP) connection. Session purity specifies whether the application wants a "brand new" session or whether the application logic is set up to reuse a "pooled" session. There are two possible values, `NEW` or `SELF`. The default is `SELF`.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_CONNECTION_PURITY_DEFAULT

          static final String CONNECTION_PROPERTY_CONNECTION_PURITY_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_CONNECTION_PURITY_ACCESSMODE

          static final byte CONNECTION_PROPERTY_CONNECTION_PURITY_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_USE_DRCP_MULTIPLE_TAG

          static final String CONNECTION_PROPERTY_USE_DRCP_MULTIPLE_TAG

      Enables multiple tagging feature in DRCP. Default value is false.
      A valid tag has to be a key value pair separated by `=` character. Multiple tags are separated by `;` character.
      Value of `key` and `value` can not be null or empty. This property is valid only for thin driver.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_USE_DRCP_MULTIPLE_TAG_DEFAULT

          static final String CONNECTION_PROPERTY_USE_DRCP_MULTIPLE_TAG_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_USE_DRCP_MULTIPLE_TAG_ACCESSMODE

          static final byte CONNECTION_PROPERTY_USE_DRCP_MULTIPLE_TAG_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DRCP_PLSQL_CALLBACK

          static final String CONNECTION_PROPERTY_DRCP_PLSQL_CALLBACK

      This is PL/SQL `"fix-up"` callback name which is provided by the application, and it is used to transform a session checked out from the pool to the desired state requested by the application.
      `"fix-up"` callback can provide performance improvements to applications by running the `"session state fix-up"` logic on the server, thereby eliminating application round-trips to the database to run the `"fix-up"` logic.
      This is an optional configuration.
      This property is valid only for thin driver.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DRCP_PLSQL_CALLBACK_DEFAULT

          static final String CONNECTION_PROPERTY_DRCP_PLSQL_CALLBACK_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_DRCP_PLSQL_CALLBACK_ACCESSMODE

          static final byte CONNECTION_PROPERTY_DRCP_PLSQL_CALLBACK_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_FORCE_DNS_LOAD_BALANCING

          static final String CONNECTION_PROPERTY_THIN_FORCE_DNS_LOAD_BALANCING

      When a hostname resolves to multiple addresses, the JDBC thin driver retrieves an array of addresses by calling "InetAddress.getAllByName()" and attempts to connect to first address in the array. If the connection fails, it tries to connect to the second address and so on.

      By default, because "InetAddress.getAllByName()" always returns the addresses in the same order, the first connection attempt will always be made to the same IP address. This defeats the goal of SCAN (Single Client Access Name which is a 11.2 RAC feature). In order to force the the driver to make the first connection attempt to a different IP address each time, you can set this property to "true". The default value is "false".

      When this connection is set to "true", the array of IP addresses that a hostname resolves to, will be rotated by one for each new JDBC connection. As a result, DNS load balancing will happen properly.

      **This is a JDBC thin driver property only.**

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_FORCE_DNS_LOAD_BALANCING_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_FORCE_DNS_LOAD_BALANCING_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_FORCE_DNS_LOAD_BALANCING_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_FORCE_DNS_LOAD_BALANCING_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_TEMP_LOB_REF_COUNT

          static final String CONNECTION_PROPERTY_ENABLE_TEMP_LOB_REF_COUNT

      By default the JDBC thin driver counts the temp LOB references and only closes them on the server when this count is down to zero. For example it may happen that two instances of CLOB (or OracleClob) A and B point to the same temp lob. At this point thin's temp lob ref count is 2. If you close A, no roundtrip will be issued because B is still holding on the temp LOB (counts is 1). Thin will send a close to the database only when B is also closed.

      The JDBC Thin driver will tell the server that it's counting temp lob references so that the server's temp lob ref count is always 1 as long as a close hasn't been issued.

      If you're running into `ORA-22922: NONEXISTENT LOB VALUE` errors in your application you should make sure that you haven't accidentally set this property to *false*.

      **This property applies to the JDBC Thin driver only. It's new in 11.2.0.3.**

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_TEMP_LOB_REF_COUNT_DEFAULT

          static final String CONNECTION_PROPERTY_ENABLE_TEMP_LOB_REF_COUNT_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_TEMP_LOB_REF_COUNT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_ENABLE_TEMP_LOB_REF_COUNT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_NET_KEEPALIVE

          static final String CONNECTION_PROPERTY_NET_KEEPALIVE

      Sets keepAlive on the Connection Socket.

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_NET_KEEPALIVE_DEFAULT

          static final String CONNECTION_PROPERTY_NET_KEEPALIVE_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_NET_KEEPALIVE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_NET_KEEPALIVE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_SQL_TRANSLATION_PROFILE

          static final String CONNECTION_PROPERTY_SQL_TRANSLATION_PROFILE

      The string identifier for the translation profile or the translator to be used. Presence of this property activates the support for SQL Translation and is thus mandatory if SQL Translation feature is required.

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_SQL_TRANSLATION_PROFILE_DEFAULT

          static final String CONNECTION_PROPERTY_SQL_TRANSLATION_PROFILE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_SQL_TRANSLATION_PROFILE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_SQL_TRANSLATION_PROFILE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_SQL_ERROR_TRANSLATION_FILE

          static final String CONNECTION_PROPERTY_SQL_ERROR_TRANSLATION_FILE

      Path to an xml file which provides the Error code translations for those errors which occur if a connection can not be established to the server. The XML file is to be provided by the user and must conform to the following DTD. This is an optional property and if not provided then untranslated exceptions with oracle error codes are thrown. This property only affects the exceptions which happen when a connection to the server cannot be established. Once connection is established the translation happens on the server bypassing the local error translation file.

          <!DOCTYPE LocalTranslationProfile[
          <!ELEMENT LocalTranslationProfile (Exception+)>
          <!ELEMENT Exception (ORAError, ErrorCode, SQLState )>
          <!ELEMENT ORAError (#PCDATA)>
          <!ELEMENT ErrorCode (#PCDATA)>
          <!ELEMENT SQLState (#PCDATA)>
          ]>



      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_SQL_ERROR_TRANSLATION_FILE_DEFAULT

          static final String CONNECTION_PROPERTY_SQL_ERROR_TRANSLATION_FILE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_SQL_ERROR_TRANSLATION_FILE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_SQL_ERROR_TRANSLATION_FILE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_RESULTSET_CACHE

          static final String CONNECTION_PROPERTY_ENABLE_RESULTSET_CACHE

      This property is ignored in 18c.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_RESULTSET_CACHE_DEFAULT

          static final String CONNECTION_PROPERTY_ENABLE_RESULTSET_CACHE_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_RESULTSET_CACHE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_ENABLE_RESULTSET_CACHE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_QUERY_RESULT_CACHE

          static final String CONNECTION_PROPERTY_ENABLE_QUERY_RESULT_CACHE

      This property is introduced in 18c. If set to false, this property turns off the ResultSet Cache feature of the JDBC Thin driver. To use this feature the server-side initialization parameter CLIENT_RESULT_CACHE_SIZE also has to be configured to a non zero value. This value controls how much memory the Thin driver can use for its cache.
      A read-only or read-mostly table can then be annoted (`RESULT_CACHE(MODE FORCE)` for example) for its data to be cached on the driver. You can also use a SQL hint `/*+result_cache */` to identify queries that are worth being cached.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_QUERY_RESULT_CACHE_DEFAULT

          static final String CONNECTION_PROPERTY_ENABLE_QUERY_RESULT_CACHE_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_QUERY_RESULT_CACHE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_ENABLE_QUERY_RESULT_CACHE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_BACKWARD_COMPATIBLE_UPDATEABLE_RESULTSET

          static final String CONNECTION_PROPERTY_BACKWARD_COMPATIBLE_UPDATEABLE_RESULTSET

      If set to true, use the old, pre 12.1.0.2.0, updateable ResultSet behavior. If false use JDBC standard compliant updateable ResultSet behavior.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_BACKWARD_COMPATIBLE_UPDATEABLE_RESULTSET_DEFAULT

          static final String CONNECTION_PROPERTY_BACKWARD_COMPATIBLE_UPDATEABLE_RESULTSET_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_BACKWARD_COMPATIBLE_UPDATEABLE_RESULTSET_ACCESSMODE

          static final byte CONNECTION_PROPERTY_BACKWARD_COMPATIBLE_UPDATEABLE_RESULTSET_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ALLOWED_LOGON_VERSION

          static final String CONNECTION_PROPERTY_ALLOWED_LOGON_VERSION

      Minimum authentication protocol required by the client. The term VERSION in the parameter name refers to the version of the authentication protocol, not the Oracle Database release. If the database doesn't meet or exceed the value defined by this parameter, then JDBC throws ORA-17292 : No valid logon method found. Allowed values :

      - 12a
      - 12
      - 11
      - 10
      - 8

      Thus if client sets the allowedLogonVersion to be 10. Then connection would fail if the database server doesn support authentication protocol 10 or above ie 11, 12 and 12a. And similarly for other values. Default logon version for JDBC thin is 8. These values are JDBC thin counterpart of SQLNET.ALLOWED_LOGON_VERSION_CLIENT. For more information on the logon values and authentication protocol, read the documenation for SQLNET.ALLOWED_LOGON_VERSION_CLIENT and SQLNET.ALLOWED_LOGON_VERSION_SERVER.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ALLOWED_LOGON_VERSION_DEFAULT

          static final String CONNECTION_PROPERTY_ALLOWED_LOGON_VERSION_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ALLOWED_LOGON_VERSION_ACCESSMODE

          static final byte CONNECTION_PROPERTY_ALLOWED_LOGON_VERSION_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_COMMIT_OPTION

          static final String CONNECTION_PROPERTY_COMMIT_OPTION

      This connection property lets you define a default commit option that will be used when calling `connection.commit();`. This can be useful in cases where you don't want to rewrite your application to specify a commit option at the call level, such as `connection.commit(myCommitOption);`.
      This property can be set at the system level (all connections will use it) or at the connection level (only that particular connection will be affected). A call level commit option will override the default value.

      Note that by default, if you don't set this property, the commit option is '0', zero, and the Oracle server's defaults apply. These defaults are: IMMEDIATE and WAIT (IO operations are done immediately and the call waits until the operation has completed to return).

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_COMMIT_OPTION_DEFAULT

          static final String CONNECTION_PROPERTY_COMMIT_OPTION_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_COMMIT_OPTION_ACCESSMODE

          static final byte CONNECTION_PROPERTY_COMMIT_OPTION_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DOWN_HOSTS_TIMEOUT

          static final String CONNECTION_PROPERTY_DOWN_HOSTS_TIMEOUT

      To specify the amount of time in seconds that information about the `down` state of server hosts is kept in driver's cache.

      The driver discovers the `down` state of server hosts when attempting connections. When a connection attempt fails, the information about the `down` state of the server host is added to the driver's cache. Subsequent connection attempts moves the `down` hosts to the end of the address list, thereby reducing the priority of such hosts. When the time specified by the `oracle.net.DOWN_HOSTS_TIMEOUT` parameter has passed, the host is purged from the driver's cache, and its priority in the address list is restored.

      Default value is 600 seconds.

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DOWN_HOSTS_TIMEOUT_DEFAULT

          static final String CONNECTION_PROPERTY_DOWN_HOSTS_TIMEOUT_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DOWN_HOSTS_TIMEOUT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_DOWN_HOSTS_TIMEOUT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_FAN_ENABLED

          static final String CONNECTION_PROPERTY_FAN_ENABLED

      Specifies whether driver High Availability (HA) or FAN (Fast Application Notification) is enabled.
      This property can be set at the system level (which applies to all connections), or at the connection level (which applies to a particular connection). The property is applicable to THIN and JDBC-OCI drivers only.

      By default, if you don't set this property, FAN/HA is enabled. The primary use of this property is to disable driver HA/FAN.

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_FAN_ENABLED_DEFAULT

          static final String CONNECTION_PROPERTY_FAN_ENABLED_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_FAN_ENABLED_ACCESSMODE

          static final byte CONNECTION_PROPERTY_FAN_ENABLED_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_TNS_ADMIN

          static final String CONNECTION_PROPERTY_TNS_ADMIN

      This property is used for setting the TNS Admin path. When using TNS Names with JDBC Thin driver this property has to be set to the directory which contains the `tnsnames.ora` file.
      This property can also be used to set the path of a properties file. When set, the driver will look for a file named `ojdbc.properties` in the TNS Admin directory.
      See Also:
      `CONNECTION_PROPERTY_CONFIG_FILE`, [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_TNS_ADMIN_DEFAULT

          static final String CONNECTION_PROPERTY_TNS_ADMIN_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_TNS_ADMIN_ACCESSMODE

          static final byte CONNECTION_PROPERTY_TNS_ADMIN_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_NETWORK_COMPRESSION

          static final String CONNECTION_PROPERTY_NETWORK_COMPRESSION

      Enables compression of the protocol data sent over network. The value can be either `"on"` , `"off"` or `"auto"`. The default value is `"off"`.

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_NETWORK_COMPRESSION_DEFAULT

          static final String CONNECTION_PROPERTY_NETWORK_COMPRESSION_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_NETWORK_COMPRESSION_ACCESSMODE

          static final byte CONNECTION_PROPERTY_NETWORK_COMPRESSION_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_NETWORK_COMPRESSION_LEVELS

          static final String CONNECTION_PROPERTY_NETWORK_COMPRESSION_LEVELS

      The value is a comma separated list of supported levels in the user preference order surrounded by brackets. The value is used at the time of negotiation to check what levels can be supported by both the client and the server and decide on the first common match. Thin driver only supports `("high")` compression level and it is the default value, so setting this property is optional.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_NETWORK_COMPRESSION_LEVELS_DEFAULT

          static final String CONNECTION_PROPERTY_NETWORK_COMPRESSION_LEVELS_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_NETWORK_COMPRESSION_LEVELS_ACCESSMODE

          static final byte CONNECTION_PROPERTY_NETWORK_COMPRESSION_LEVELS_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_NETWORK_COMPRESSION_THRESHOLD

          static final String CONNECTION_PROPERTY_NETWORK_COMPRESSION_THRESHOLD

      Minimum size of data in packet required to perform compression. Packet compression will not be done if size of data to be sent in the packet is less than specified value. The default is `"1024"`. The value cannot be less than `"200"`. The value is in bytes.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_NETWORK_COMPRESSION_THRESHOLD_DEFAULT

          static final String CONNECTION_PROPERTY_NETWORK_COMPRESSION_THRESHOLD_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_NETWORK_COMPRESSION_THRESHOLD_ACCESSMODE

          static final byte CONNECTION_PROPERTY_NETWORK_COMPRESSION_THRESHOLD_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_CONFIG_FILE

          static final String CONNECTION_PROPERTY_CONFIG_FILE

      This property provides the location of one or more properties files. When a connection is opened, the driver will read connection properties from these files. This feature is not supported for connections made by the server-side internal driver.
      A file location can be a simple path: "path/to/my/file", or a platform neutral file URI: "file:///path/to/my/file".
      Multiple files can be given as a comma delimited list: "fileOne, fileTwo, fileThree". The list may contain the value "default", which will be resolved as the default locations described below. Higher precedence is given to files which appear later in the list. In the example, a property defined in fileThree would override fileTwo's definition of that property. Likewise, fileTwo's definitions can override fileOne's.
      This feature can be explictly disabled by setting this property to an empty string.

      **Default File Locations**
      If oracle.jdbc.config.file is not set, the driver will attempt to read from a default location: \$TNS_ADMIN/ojdbc.properties. Here, \$TNS_ADMIN can refer to "TNS_ADMIN" set as a system property or environment variable. It can also refer to the connection property `CONNECTION_PROPERTY_TNS_ADMIN`. If the connection property is set, the driver will use that value rather than the system property or environment variable. If the connection property is not set, "TNS_ADMIN" as a system property will override the environment variable.
      If a tnsnames alias is used to connect, the driver will also attempt to read from \$TNS_ADMIN/ojdbc\_\<alias\>.properties, where \<alias\> is the name given in the connection string. For example: A DataSource configured with "jdbc:oracle:thin:@*orcl*" would read connection properties from \$TNS_ADMIN/ojdbc\_*orcl*.properties, in addition to \$TNS_ADMIN/ojdbc.properties. A property defined in ojdbc_orcl.properties would override ojdbc.properties' definition of that property. If ojdbc.properties does not exist, then properties will only be read from ojdbc\_\<alias\>.properties.
      There is no requirement that any of the default files actually exist. If the driver can not locate one of the default files, or it can not resolve the value of \$TNS_ADMIN, it will still attempt to connect with any properties provided by alternative sources such as system propeties or a Properties object.

      **Properties File Syntax**
      Files are read according to the "simple line-oriented format" described in the JavaDoc of [`Properties.load(java.io.Reader)`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true#load_java_io_Reader_). Any property which has ACCESSMODE_FILEPROP can be defined in a file.
      The basic properties file format is extended to support environment variable and system property evaluation. These evaluated expressions can appear within the value of a property, but not the name. The syntax and meaning of evaluated expressions are as follows:
      1.  "\${xyz}" is replaced with a system property or environment variable named "xyz". The environment variable is used only if the system property is not defined. If neither are defined, the driver will throw a SQLException.
      2.  "?" is replaced with the value of the ORACLE_HOME environment variable. If the environment variable is not defined, the driver will throw a SQLException.
      3.  "\${/}" is replaced with the file system's path separator. "path\${/}to\${/}" is replaced with "path/to/" on Linux, and "path\to\\ on Windows.
      4.  Two consecutive special characters will escape evaluation.
          - "\$\${xyz}" is replaced with "\${xyz}"
          - "??abc" is replaced with "?abc"


      **Precedence**
      An order of precedence is applied when connection properties are defined by multiple sources. A property's value will always be resolved by the source which has the highest precedence. The sources of connection properties, ranked from highest to lowest precedence are:
      1.  A Properties object passed to OracleDataSource, DriverManager, etc.
      2.  The jar-internal properties file: defaultConnectionProperties.properties in the oracle.jdbc package
      3.  Java system properties
      4.  An external properties file: A default under \$TNS_ADMIN, or one given by oracle.jdbc.config.file
      5.  The default value of a property, as specified by the CONNECTION_PROPERTY\_{name}\_DEFAULT constants

      See Also:
      [`Properties.load(Reader)`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true#load_java_io_Reader_), `ACCESSMODE_FILEPROP`, [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_CONFIG_FILE_DEFAULT

          static final String CONNECTION_PROPERTY_CONFIG_FILE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_CONFIG_FILE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_CONFIG_FILE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_WEBSOCKET_USER

          static final String CONNECTION_PROPERTY_WEBSOCKET_USER

      This connection property is used to configure the username of the webserver, when the JDBC Thin driver is configured to connect to a webserver using the `Secure Websocket protocol (WSS)`.
      The webserver acts as a reverse proxy for the Oracle Database.
      The default value of this property is `null`.
      See Also:
      `CONNECTION_PROPERTY_WEBSOCKET_PASSWORD`, [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_WEBSOCKET_USER_DEFAULT

          static final String CONNECTION_PROPERTY_WEBSOCKET_USER_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_WEBSOCKET_USER_ACCESSMODE

          static final byte CONNECTION_PROPERTY_WEBSOCKET_USER_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_WEBSOCKET_PASSWORD

          static final String CONNECTION_PROPERTY_WEBSOCKET_PASSWORD

      This connection property is used to configure the password of the webserver, when the JDBC Thin driver is configured to connect to a webserver using the `Secure Websocket protocol (WSS)`.
      The webserver acts as a reverse proxy for the Oracle Database.
      The default value of this property is `null`.
      See Also:
      `CONNECTION_PROPERTY_WEBSOCKET_USER`, [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_WEBSOCKET_PASSWORD_DEFAULT

          static final String CONNECTION_PROPERTY_WEBSOCKET_PASSWORD_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_WEBSOCKET_PASSWORD_ACCESSMODE

          static final byte CONNECTION_PROPERTY_WEBSOCKET_PASSWORD_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULT_CONNECTION_VALIDATION

          static final String CONNECTION_PROPERTY_DEFAULT_CONNECTION_VALIDATION

      This connection property is used to specify how much effort to put into validating a [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true).
      This property controls what isValid() does.
      The possible values for this property are - "NONE", "LOCAL", "SOCKET", "NETWORK", "SERVER" and "COMPLETE".
      The values are case-sensitive, setting any other value throws exception.
      The default value of this property is "NETWORK".
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULT_CONNECTION_VALIDATION_DEFAULT

          static final String CONNECTION_PROPERTY_DEFAULT_CONNECTION_VALIDATION_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_DEFAULT_CONNECTION_VALIDATION_ACCESSMODE

          static final byte CONNECTION_PROPERTY_DEFAULT_CONNECTION_VALIDATION_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_IMPLICIT_REQUESTS

          static final String CONNECTION_PROPERTY_ENABLE_IMPLICIT_REQUESTS

      Specifies whether to enable implicit request boundary support for Application Continuity (AC).
      Implicit request support helps to reduce application failover recovery time. This AC optimization should be used with caution for applications that change server session states during a request. For more details, please consult the JDBC and RAC documentations on Auto-AC.

      This property can be set at the system level (which applies to all connections), or at the connection level (which applies to a particular connection). The property is applicable to THIN driver only.

      By default, the value of this property is "true", which means that implicit request support is enabled.

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_IMPLICIT_REQUESTS_DEFAULT

          static final String CONNECTION_PROPERTY_ENABLE_IMPLICIT_REQUESTS_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_IMPLICIT_REQUESTS_ACCESSMODE

          static final byte CONNECTION_PROPERTY_ENABLE_IMPLICIT_REQUESTS_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_ALLOW_WEAK_CRYPTO

          static final String CONNECTION_PROPERTY_THIN_NET_ALLOW_WEAK_CRYPTO

      Starting in release 23, the driver can be configured to use strong session keys and weak ciphers can be disabled when *Native Network Encryption* is used. But this breaks compatibility with older versions of the server which may not have the same capability. An exception with error code `12268` is thrown when server does not have this capabilty. By default, in order to allow compatibility with such servers, and at the cost of security, this property is set to "true". When this property is configured to "false" then strong session keys are used and the following algorithms are disabled. Disabled Encryption algorithms : RC4_40, DES40, DES, RC4_56, RC4_128, 3DES112, 3DES168 and RC4_256. Disabled Checksum algorithms : MD5. This property can also be configured through URL. The value configured through URL has higher priority than the value configured through connection properties. Please see the below examples to know how to configure this property through URL.
      EzConnectPlus Format:
      jdbc:oracle:thin:@//host:port/servicename?allow_weak_crypto=false
      TNS Long URL Format:
      jdbc:oracle:thin:@(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=host)(PORT=5521))(CONNECT_DATA= (SERVICE_NAME=servicename))(Security=(ALLOW_WEAK_CRYPTO=false)))
      Since:
      23c

      See Also:
      `CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_LEVEL`, `CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_TYPES`, `CONNECTION_PROPERTY_THIN_NET_CHECKSUM_TYPES`, `//_end_m4_ifInServer`, [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_ALLOW_WEAK_CRYPTO_DEFAULT

          static final String CONNECTION_PROPERTY_THIN_NET_ALLOW_WEAK_CRYPTO_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_THIN_NET_ALLOW_WEAK_CRYPTO_ACCESSMODE

          static final byte CONNECTION_PROPERTY_THIN_NET_ALLOW_WEAK_CRYPTO_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_AC_SUPPORT

          static final String CONNECTION_PROPERTY_ENABLE_AC_SUPPORT

      Specifies whether driver support for Application Continuity (AC) is enabled.
      This property can be set at the system level (which applies to all connections), or at the connection level (which applies to a particular connection). The property is applicable to THIN driver only.

      By default, if you don't set this property, AC support is enabled on the JDBC driver data sources. The primary use of this property is to disable AC on the data sources.

      Note that when this property is set to true, whether AC is actually active depends on other factors like server AC configuration. //\_end_m4_ifInServer

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_AC_SUPPORT_DEFAULT

          static final String CONNECTION_PROPERTY_ENABLE_AC_SUPPORT_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_AC_SUPPORT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_ENABLE_AC_SUPPORT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_TG_SUPPORT

          static final String CONNECTION_PROPERTY_ENABLE_TG_SUPPORT

      Specifies whether driver support for Transaction Guard (TG) is enabled.
      This property can be set at the system level (which applies to all connections), or at the connection level (which applies to a particular connection). The property is applicable to THIN driver only.

      By default, if you don't set this property, TG support is disabled on the JDBC driver data sources, unless Application Continuity (AC) is enabled. The primary use of this property is to enable TG on the data sources, when AC is not enabled.

      Note that when this property is set to true, whether TG is actually active depends on other factors like server TG configuration. One way to check if TG is actually enabled is to call `getLogicalTransactionId` on `oracle.jdbc.OracleConnection` and verify that the returned value is not null. //\_end_m4_ifInServer

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_TG_SUPPORT_DEFAULT

          static final String CONNECTION_PROPERTY_ENABLE_TG_SUPPORT_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ENABLE_TG_SUPPORT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_ENABLE_TG_SUPPORT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_REQUEST_SIZE_LIMIT

          static final String CONNECTION_PROPERTY_REQUEST_SIZE_LIMIT

      Specifies the maximum request size, in terms of number of JDBC calls, beyond which AC replay will be disabled. For example, if the property value is set to 100, it means replay will be disabled for any request with more than 100 JDBC calls in it.
      We recommend that applicationss do not set this property unless there is a demonstrated memory size problem caused by request size and no better solution is feasible.

      Replay disabling applies only to any request that exceeds the limit. Replay will be reenabled at the next beginRequest on the same JDBC physical connection.

      This property can be set at the system level (which applies to all connections), or at the connection level (which applies to a particular connection). The property is applicable to THIN driver only.

      There is a request-size histogram in the AC statistics that users can use to get an idea of the request size distribution of their application. It can be obtained by calling `getRequestSizeHistogram()` on `oracle.jdbc.replay.ReplayStatistics`.

      The histogram is also dumped into the Oracle JDBC driver logs, when the driver detects significant memory pressure.

      Users can use the histogram and AC statistics to determine the majority of their request sizes, and set the request-size limit to be slightly above those. For small number of long requests above the limit, users could consider alternatives such as more frequent connection pool checkout/checkin's, deploying Transparent Application Continuity (TAC) to reduce request size, or to allow replay being disabled for requests with only long queries.

      By default, the value of this property is "2147483647", which is Integer.MAX_VALUE that means replay is practically enabled for all requests.

      Since:
      20.1 //\_end_m4_ifInServer

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_REQUEST_SIZE_LIMIT_DEFAULT

          static final String CONNECTION_PROPERTY_REQUEST_SIZE_LIMIT_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_REQUEST_SIZE_LIMIT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_REQUEST_SIZE_LIMIT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_IN_BAND_NOTIFICATION

          static final String CONNECTION_PROPERTY_IN_BAND_NOTIFICATION

      Specifies whether driver in-band notification support is enabled. This feature primarily helps applications to drain connections gracefully during Oracle Autonomous Database (ADB) and Real Application Clusters (RAC) planned maintenance.

      This property can be set at the system level (which applies to all connections), or at the connection level (which applies to a particular connection). The property is applicable to THIN and JDBC-OCI drivers only.

      By default, if you don't set this property, in-band notification is always enabled. The primary use of this property is to disable this feature, which might be necessary in case in-band notification interferes with similar features in upper-stacks (like a connection pool or application container), or malfunctions.

      //\_end_m4_ifInServer
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_IN_BAND_NOTIFICATION_DEFAULT

          static final String CONNECTION_PROPERTY_IN_BAND_NOTIFICATION_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_IN_BAND_NOTIFICATION_ACCESSMODE

          static final byte CONNECTION_PROPERTY_IN_BAND_NOTIFICATION_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_TOKEN_AUTHENTICATION

          static final String CONNECTION_PROPERTY_TOKEN_AUTHENTICATION

      Enables the use of access tokens that are stored in a file system location when authenticating with Oracle Database.

      In this release of Oracle JDBC, "OCI_TOKEN" and "OAUTH" are the only accepted values for this property. Setting this property to "OCI_TOKEN" or "OAUTH" configures Oracle JDBC to obtain tokens from the file system as described in the JavaDoc of `CONNECTION_PROPERTY_TOKEN_LOCATION`.

      If an Oracle Net Descriptor style URL includes the TOKEN_AUTH parameter then the value of that parameter takes precedence over a value defined by this property.

      If a username and password are provided, then Oracle JDBC will use them to authenticate with the database, and this property is ignored.

      If a token is configured using `CONNECTION_PROPERTY_ACCESS_TOKEN`, then Oracle JDBC will use it to authenticate with the database, and this property is ignored.

      Since:
      23

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_TOKEN_AUTHENTICATION_DEFAULT

          static final String CONNECTION_PROPERTY_TOKEN_AUTHENTICATION_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_TOKEN_AUTHENTICATION_ACCESSMODE

          static final byte CONNECTION_PROPERTY_TOKEN_AUTHENTICATION_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_TOKEN_LOCATION

          static final String CONNECTION_PROPERTY_TOKEN_LOCATION

      When `CONNECTION_PROPERTY_TOKEN_AUTHENTICATION` is set to "OCI_TOKEN" or "OAUTH", this property specifies the file system path to obtain access tokens from. The path specified by this property must be a directory containing a file named "token", and the token file must contain a JSON Web Token (JWT) on a single line of UTF-8 encoded text. The JWT format is specified by [RFC 7519](https://datatracker.ietf.org/doc/html/rfc7519).

      - If the value of `CONNECTION_PROPERTY_TOKEN_AUTHENTICATION` is "OCI_TOKEN" then the path given by this property must be a directory containing a both a token file, and a file named "oci_db_key.pem" that stores the proof-of-possession key for the JWT token. The private key file must use the PEM format and must contain the base64 encoding of an RSA private key in the PKCS#8 format. The private key encoding must appear between the tags "-----BEGIN PRIVATE KEY---" and "-----END PRIVATE KEY-----". Oracle JDBC uses the private key to demonstrate proof of possession. Proof of possession is specified by [RFC 7800](https://datatracker.ietf.org/doc/html/rfc7800).

        *Note that the OCI CLI tool may be used to generate both the token and private key files.* By default, the OCI CLI tool will write these files to the location of `$HOME/.oci/db-token/`. If the value of `CONNECTION_PROPERTY_TOKEN_AUTHENTICATION` is "OCI_TOKEN", and no location is configured by this property, then Oracle JDBC will read the token and private key files from the default location of `$HOME/.oci/db-token/`.

      - If the value of `CONNECTION_PROPERTY_TOKEN_AUTHENTICATION` is "OAUTH", then only the token file is required, and the path given by this property may locate either a file or directory. If a file is located, then the JWT is read from it. Otherwise, if a directory is located, then the JWT is read from a file named "token" in that directory.

      If an Oracle Net Descriptor style URL includes the TOKEN_LOCATION parameter then the value of that parameter takes precedence over a value defined by this property.

      Since:
      23

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_TOKEN_LOCATION_DEFAULT

          static final String CONNECTION_PROPERTY_TOKEN_LOCATION_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_TOKEN_LOCATION_ACCESSMODE

          static final byte CONNECTION_PROPERTY_TOKEN_LOCATION_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION

          static final String CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION

      Configures how Oracle JDBC performs authentication with a user name and password.

      In this release of Oracle JDBC, "PASSWORD_VERIFIER" and "OCI_TOKEN" are the only accepted values for this property.

      If the value is "PASSWORD_VERIFIER", then [database authentication](https://docs.oracle.com/en/database/oracle/oracle-database/21/dbseg/configuring-authentication.html#GUID_1F783131_CD1C_4EA0_9300_C132651B0700) is performed.

      If the value is "OCI_TOKEN", then authentication is performed with the Oracle Identity Cloud Service as described in `CONNECTION_PROPERTY_OCI_IAM_URL`

      The default value of this property is "PASSWORD_VERIFIER".

      If an Oracle Net Descriptor style URL includes the PASSWORD_AUTH parameter then the value of that parameter takes precedence over a value defined by this property.

      Since:
      23

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION_DEFAULT

          static final String CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION_DEFAULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION_ACCESSMODE

          static final byte CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_IAM_URL

          static final String CONNECTION_PROPERTY_OCI_IAM_URL

      When `CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION` is set to "OCI_TOKEN", this property must specify the full path of the Identity and Access Management (IAM) endpoint that Oracle JDBC authenticates with, as in:

              https://{iam-endpoint}/{version}/dbBearerToken


      Oracle JDBC must be configured to trust the certificate of the server located by this URL. Certificates signed by an authority included in the JDK's default cacerts file will be trusted. Additional trusted certificates may be configued with `CONNECTION_PROPERTY_WALLET_LOCATION`, `CONNECTION_PROPERTY_THIN_JAVAX_NET_SSL_TRUSTSTORE`.

      If an Oracle Net Descriptor style URL includes the OCI_IAM_URL parameter, then the value of that parameter takes precedence over a value defined by this property.

      Since:
      23

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_IAM_URL_DEFAULT

          static final String CONNECTION_PROPERTY_OCI_IAM_URL_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_IAM_URL_ACCESSMODE

          static final byte CONNECTION_PROPERTY_OCI_IAM_URL_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_TENANCY

          static final String CONNECTION_PROPERTY_OCI_TENANCY

      When `CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION` is set to "OCI_TOKEN", this property must specify the Oracle Cloud ID (OCID) of the cloud tenant for the user that Oracle JDBC authenticates as.

      If an Oracle Net Descriptor style URL includes the OCI_TENANCY parameter, then the value of that parameter takes precedence over a value defined by this property.

      Since:
      23

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_TENANCY_DEFAULT

          static final String CONNECTION_PROPERTY_OCI_TENANCY_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_TENANCY_ACCESSMODE

          static final byte CONNECTION_PROPERTY_OCI_TENANCY_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_COMPARTMENT

          static final String CONNECTION_PROPERTY_OCI_COMPARTMENT

      When `CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION` is set to "OCI_TOKEN", this property specifies the Oracle Cloud ID (OCID) of the compartment for the database identified by `CONNECTION_PROPERTY_OCI_DATABASE`. If this property is not set, then Oracle JDBC requests access to all databases within the tenancy identified by `CONNECTION_PROPERTY_OCI_TENANCY`.

      If an Oracle Net Descriptor style URL includes the OCI_COMPARTMENT parameter, then the value of that parameter takes precedence over a value defined by this property.

      Since:
      23

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_COMPARTMENT_DEFAULT

          static final String CONNECTION_PROPERTY_OCI_COMPARTMENT_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_COMPARTMENT_ACCESSMODE

          static final byte CONNECTION_PROPERTY_OCI_COMPARTMENT_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_DATABASE

          static final String CONNECTION_PROPERTY_OCI_DATABASE

      When `CONNECTION_PROPERTY_PASSWORD_AUTHENTICATION` is set to "OCI_TOKEN", this property specifies the Oracle Cloud ID (OCID) of the database that JDBC requests access to. If this property is not set, then Oracle JDBC requests access to all databases within the compartment specified by `CONNECTION_PROPERTY_OCI_COMPARTMENT`.

      If an Oracle Net Descriptor style URL includes the OCI_DATABASE parameter, then the value of that parameter takes precedence over a value defined by this property.

      Since:
      23

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_DATABASE_DEFAULT

          static final String CONNECTION_PROPERTY_OCI_DATABASE_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_OCI_DATABASE_ACCESSMODE

          static final byte CONNECTION_PROPERTY_OCI_DATABASE_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ACCESS_TOKEN

          static final String CONNECTION_PROPERTY_ACCESS_TOKEN

      This property configures an access token that Oracle JDBC uses for authentication with Oracle Database. An access token configured with this property will only be used if neither a user name nor password has been provided when creating a new connection. If a user name or a password is provided, via connection properties, programmatic APIs, or by any other means, then the value of this property is ignored.

      If a value is configured for this property, then Oracle JDBC will ignore any token that is specified by `CONNECTION_PROPERTY_TOKEN_AUTHENTICATION` and `CONNECTION_PROPERTY_TOKEN_LOCATION`.

      The value of this property must be a JSON Web Token (JWT). The JWT format is specified by [RFC 7519](https://datatracker.ietf.org/doc/html/rfc7519).

      The database instance that Oracle JDBC connects to must be configured to validate the token with the service that issued it. The Oracle Database Security Guide specifies how to configure the database for token based authentication.

      On systems where access tokens are stored in environment variables, it may be useful to note that an ojdbc.properties file can include expressions that resolve to the value of an environment variable. For example, this line in ojdbc.properties would configure this property as the value of an environment variable named "DATABASE_ACCESS_TOKEN":

              oracle.jdbc.accessToken=${DATABASE_ACCESS_TOKEN}


      Since:
      23

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_ACCESS_TOKEN_DEFAULT

          static final String CONNECTION_PROPERTY_ACCESS_TOKEN_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_ACCESS_TOKEN_ACCESSMODE

          static final byte CONNECTION_PROPERTY_ACCESS_TOKEN_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_PASSWORD

          static final String CONNECTION_PROPERTY_PASSWORD

      The value of this property is used as the password when connecting to the database.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_PASSWORD_DEFAULT

          static final String CONNECTION_PROPERTY_PASSWORD_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_PASSWORD_ACCESSMODE

          static final byte CONNECTION_PROPERTY_PASSWORD_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_SERVER

          static final String CONNECTION_PROPERTY_SERVER

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_PROPERTY_SERVER_DEFAULT

          static final String CONNECTION_PROPERTY_SERVER_DEFAULT

    <!-- -->

    - #### CONNECTION_PROPERTY_SERVER_ACCESSMODE

          static final byte CONNECTION_PROPERTY_SERVER_ACCESSMODE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DATABASE_OK

          static final int DATABASE_OK

      Define return values for pingDatabase api The physical database connection is not closed and the database is reachable. SQL requests my succeed.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DATABASE_CLOSED

          static final int DATABASE_CLOSED

      Define return values for pingDatabase api The physical database connection is closed. SQL requests will fail.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DATABASE_NOTOK

          static final int DATABASE_NOTOK

      Define return values for pingDatabase api The physical database connection is not closed but the database is not reachable. SQL requests will fail.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DATABASE_TIMEOUT

          static final int DATABASE_TIMEOUT

      Define return values for pingDatabase api The call timed out before any positive or negative acknowledgement was received. SQL requests may or may not succeed.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### INVALID_CONNECTION

          static final int INVALID_CONNECTION

      Values used for close(int). The connection is no longer useable.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PROXY_SESSION

          static final int PROXY_SESSION

      Values used for close(int). Close the proxy session, not the entire connection
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ABANDONED_CONNECTION_CALLBACK

          static final int ABANDONED_CONNECTION_CALLBACK

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### RELEASE_CONNECTION_CALLBACK

          static final int RELEASE_CONNECTION_CALLBACK

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ALL_CONNECTION_CALLBACKS

          static final int ALL_CONNECTION_CALLBACKS

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_RELEASE_LOCKED

          static final int CONNECTION_RELEASE_LOCKED

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_RELEASE_LOW

          static final int CONNECTION_RELEASE_LOW

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNECTION_RELEASE_HIGH

          static final int CONNECTION_RELEASE_HIGH

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PROXYTYPE_USER_NAME

          static final int PROXYTYPE_USER_NAME

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PROXYTYPE_DISTINGUISHED_NAME

          static final int PROXYTYPE_DISTINGUISHED_NAME

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PROXYTYPE_CERTIFICATE

          static final int PROXYTYPE_CERTIFICATE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PROXY_TYPE

          static final String PROXY_TYPE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PROXY_USER_NAME

          static final String PROXY_USER_NAME

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PROXY_USER_PASSWORD

          static final String PROXY_USER_PASSWORD

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PROXY_DISTINGUISHED_NAME

          static final String PROXY_DISTINGUISHED_NAME

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PROXY_CERTIFICATE

          static final String PROXY_CERTIFICATE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PROXY_ROLES

          static final String PROXY_ROLES

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CLIENT_INFO_KEY_SEPARATOR

          static final String CLIENT_INFO_KEY_SEPARATOR

      Separate the namespace from the key the name of a client info. All Oracle client info names are of the form \<namespace\>.\<key\>.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OCSID_NAMESPACE

          static final String OCSID_NAMESPACE

      Special namespace for sending end-to-end metrics. There are two namespaces for sending end-to-end metrics values. This one uses the OCSID mechanism to send the values as opposed to the mechanism used for all other client info values.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OCSID_ACTION_KEY

          static final String OCSID_ACTION_KEY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OCSID_CLIENTID_KEY

          static final String OCSID_CLIENTID_KEY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OCSID_ECID_KEY

          static final String OCSID_ECID_KEY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OCSID_MODULE_KEY

          static final String OCSID_MODULE_KEY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OCSID_DBOP_KEY

          static final String OCSID_DBOP_KEY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OCSID_SEQUENCE_NUMBER_KEY

          static final String OCSID_SEQUENCE_NUMBER_KEY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### END_TO_END_ACTION_INDEX

          static final int END_TO_END_ACTION_INDEX

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### END_TO_END_CLIENTID_INDEX

          static final int END_TO_END_CLIENTID_INDEX

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### END_TO_END_ECID_INDEX

          static final int END_TO_END_ECID_INDEX

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### END_TO_END_MODULE_INDEX

          static final int END_TO_END_MODULE_INDEX

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### END_TO_END_STATE_INDEX_MAX

          static final int END_TO_END_STATE_INDEX_MAX

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NETWORK_COMPRESSION_OFF

          static final String NETWORK_COMPRESSION_OFF

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NETWORK_COMPRESSION_ON

          static final String NETWORK_COMPRESSION_ON

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NETWORK_COMPRESSION_AUTO

          static final String NETWORK_COMPRESSION_AUTO

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NETWORK_COMPRESSION_LEVEL_LOW

          static final String NETWORK_COMPRESSION_LEVEL_LOW

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NETWORK_COMPRESSION_LEVEL_LOW_VALUE

          static final int NETWORK_COMPRESSION_LEVEL_LOW_VALUE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NETWORK_COMPRESSION_LEVEL_HIGH

          static final String NETWORK_COMPRESSION_LEVEL_HIGH

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NETWORK_COMPRESSION_LEVEL_HIGH_VALUE

          static final int NETWORK_COMPRESSION_LEVEL_HIGH_VALUE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NETWORK_COMPRESSION_THRESHOLD_MIN

          static final int NETWORK_COMPRESSION_THRESHOLD_MIN

      Minimum value supported by the connection property `CONNECTION_PROPERTY_NETWORK_COMPRESSION_THRESHOLD`. The value is in bytes.

      See Also:
      `CONNECTION_PROPERTY_NETWORK_COMPRESSION_THRESHOLD`, [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CACHE_SIZE_NOT_SET

          static final int CACHE_SIZE_NOT_SET

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_TIMEOUT

          static final String NTF_TIMEOUT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_QOS_PURGE_ON_NTFN

          static final String NTF_QOS_PURGE_ON_NTFN

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_QOS_RELIABLE

          static final String NTF_QOS_RELIABLE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_QOS_SECURE

          static final String NTF_QOS_SECURE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_ASYNC_DEQ

          static final String NTF_ASYNC_DEQ

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_AQ_PAYLOAD

          static final String NTF_AQ_PAYLOAD

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_USE_SSL

          static final String NTF_USE_SSL

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_QOS_TX_ACK

          static final String NTF_QOS_TX_ACK

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_QOS_AUTO_ACK

          static final String NTF_QOS_AUTO_ACK

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_LOCAL_TCP_PORT

          static final String NTF_LOCAL_TCP_PORT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_DEFAULT_TCP_PORT

          static final int NTF_DEFAULT_TCP_PORT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_LOCAL_HOST

          static final String NTF_LOCAL_HOST

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_GROUPING_CLASS

          static final String NTF_GROUPING_CLASS

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_GROUPING_CLASS_NONE

          static final String NTF_GROUPING_CLASS_NONE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_GROUPING_CLASS_TIME

          static final String NTF_GROUPING_CLASS_TIME

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_GROUPING_VALUE

          static final String NTF_GROUPING_VALUE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_GROUPING_TYPE

          static final String NTF_GROUPING_TYPE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_GROUPING_TYPE_SUMMARY

          static final String NTF_GROUPING_TYPE_SUMMARY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_GROUPING_TYPE_LAST

          static final String NTF_GROUPING_TYPE_LAST

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_GROUPING_START_TIME

          static final String NTF_GROUPING_START_TIME

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_GROUPING_REPEAT_TIME

          static final String NTF_GROUPING_REPEAT_TIME

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NTF_GROUPING_REPEAT_FOREVER

          static final String NTF_GROUPING_REPEAT_FOREVER

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DCN_NOTIFY_ROWIDS

          static final String DCN_NOTIFY_ROWIDS

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DCN_IGNORE_INSERTOP

          static final String DCN_IGNORE_INSERTOP

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DCN_IGNORE_UPDATEOP

          static final String DCN_IGNORE_UPDATEOP

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DCN_IGNORE_DELETEOP

          static final String DCN_IGNORE_DELETEOP

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DCN_NOTIFY_CHANGELAG

          static final String DCN_NOTIFY_CHANGELAG

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DCN_QUERY_CHANGE_NOTIFICATION

          static final String DCN_QUERY_CHANGE_NOTIFICATION

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DCN_BEST_EFFORT

          static final String DCN_BEST_EFFORT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DCN_CLIENT_INIT_CONNECTION

          static final String DCN_CLIENT_INIT_CONNECTION

      Set the value of DCN_CLIENT_INIT_CONNECTION to 'true' for using the Client initiated DCN connection. By default the value is 'false' and the DCN Connection is initiated by the Server.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DCN_USE_HOST_CONNECTION_ADDR_INFO

          static final String DCN_USE_HOST_CONNECTION_ADDR_INFO

      Set the value of DCN_USE_HOST_CONNECTION_ADDR_INFO to 'false' to use the address info returned by the server for establishing the client initiated DCN Connection. Default value is 'true' and Host connection's connection string is used for establishing the Client initiated DCN connection.
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### commit

          void commit(EnumSet<OracleConnection.CommitOption> options)
               throws SQLException

      Commits the transaction with the given options.
      Parameters:
      `flags` - commit options

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### archive

          void archive(int mode,
                       int aseq,
                       String acstext)
                throws SQLException

      Deprecated. This method will be removed in a future version.
      Not implemented.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### openProxySession

          void openProxySession(int type,
                                Properties prop)
                         throws SQLException

      Opens a new proxy session with the username provided in the prop argument and switches to this new session.

      This feature is supported for both thin and oci driver.

      Three proxy types are supported :
      - OracleConnection.PROXYTYPE_USER_NAME : In this type PROXY_USER_NAME needs to be provided in prop. The value should be a java.lang.String;
      - OracleConnection.PROXYTYPE_DISTINGUISHED_NAME : In this type PROXY_DISTINGUISHED_NAME has to be set in prop. The value is a java.lang.String object;
      - OracleConnection.PROXYTYPE_CERTIFICATE : In this type PROXY_CERTIFICATE has to be set in prop. The value is a bytep\[\] which contains the certificate.

      Roles can also be provided in the property argument. The key is OracleConnection.PROXY_ROLES. The value is a String\[\] which contains the roles.
      Parameters:
      `type` - has to be either OracleConnection.PROXYTYPE_USER_NAME or OracleConnection.PROXYTYPE_DISTINGUISHED_NAME or OracleConnection.PROXYTYPE_CERTIFICATE

      `prop` - keys/values

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getAutoClose

          boolean getAutoClose()
                        throws SQLException

      The driver is always in auto-close mode.
      Returns:
      should always return `true`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - should never been raised

      See Also:
      `setAutoClose`

    <!-- -->

    - #### getDefaultExecuteBatch

          int getDefaultExecuteBatch()

      Deprecated. As of 12.1 all APIs related to oracle-style statement batching are deprecated in favor of standard JDBC batching. We recommend using the standard model going forward as it is spec compliant and provides more information and control to the application.
      Executions are not batched but sent immediately. Oracle style of batching has been deprecated in 12.1 and made a no-op in 12.2. We recommend using the standard model of batching.
      Returns:
      the batch value, always 1.

      See Also:
      [`OraclePreparedStatement.setExecuteBatch`](OraclePreparedStatement.md), `setDefaultExecuteBatch`

    <!-- -->

    - #### getDefaultRowPrefetch

          int getDefaultRowPrefetch()

      Retrieves the value of row prefetch for all statements associated with this connection and created after this value was set.
      The row-prefetching feature associates an integer row-prefetch setting with a given statement object. JDBC fetches that number of rows at a time from the database during the query. That is, JDBC will fetch N rows that match the query criteria and bring them all back to the client at once, where N is the prefetch setting. Then, once your `next` calls have run through those N rows, JDBC will go back to fetch the next N rows that match the criteria.

      You can set the number of rows to prefetch for a particular Oracle statement (any type of statement). You can also reset the default number of rows that will be prefetched for all statements in your connection with the `setDefaultRowPrefetch` method. Therefore, the row prefetch value returned by this `getDefaultRowPrefetch` entrypoint is valid for statements for which you have not defined a different row prefetch value.

      The default number of rows to prefetch to the client is 10.

      Example where `conn` is your connection object:
      `//Get the default row-prefetch setting for this connection`
      `int defRowPref = ((OracleConnection)conn).getDefaultRowPrefetch();`

      Returns:
      the row prefetch value

      See Also:
      [`OracleStatement.setRowPrefetch`](OracleStatement.md), `setDefaultRowPrefetch`

    <!-- -->

    - #### getDescriptor

          Object getDescriptor(String sql_name)

      Gets a Descriptor object corresponding to a sql type.
      Parameters:
      `sql_name` - the sql type

      Returns:
      the Descriptor Object that matches the sql type

      See Also:
      `putDescriptor`, [`oracle.sql.TypeDescriptor`](../sql/TypeDescriptor.md)

    <!-- -->

    - #### getEndToEndMetrics

          String[] getEndToEndMetrics()
                               throws SQLException

      Deprecated. This has been deprecated since 12.1 in favor of getClientInfo(). It is not recommended to use this API intermingled with get/setClientInfo APIs.
      Gets the values of the end-to-end metrics, if any. Does not include the sequence number. If DMS is in use and metrics have been set via DMS, this method will return the metrics set via DMS, not those set via setEndToEndMetrics. The DMS metric override the metrics set by setEndToEndMetrics.
      Returns:
      a String\[\]. The indices are the END_TO_END_XXX_INDEX constants. The values are the values of the corresponding metrics.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      See Also:
      `setEndToEndMetrics`, [`Connection.getClientInfo(java.lang.String)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#getClientInfo_java_lang_String_), [`Connection.getClientInfo()`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#getClientInfo__)

    <!-- -->

    - #### getEndToEndECIDSequenceNumber

          short getEndToEndECIDSequenceNumber()
                                       throws SQLException

      Deprecated. This is deprecated since 12.1 in favor of getClientInfo(). It is not recommended to use this API intermingled with get/setClientInfo APIs.
      Gets the current end to end tracing context id sequence number. This could be any of the following values: the value passed in the most recent call to setEndToEndMetrics the value returned by the database after the most recent statement execution the value incremented by JDBC diagnostic messages the value JDBC retrieved from DMS (only in a DMS environment)
      Returns:
      the current ECID sequence number

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      See Also:
      [`Connection.getClientInfo(java.lang.String)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#getClientInfo_java_lang_String_), [`Connection.getClientInfo()`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#getClientInfo__)

    <!-- -->

    - #### getIncludeSynonyms

          boolean getIncludeSynonyms()

      Checks whether or not synonyms information is included in `DatabaseMetaData.getColumns`. By default and for performance reasons it won't but you can change this with the `setIncludeSynonyms` method.
      Returns:
      `true` if `DatabaseMetaData.getColumns` will report information if a table synonym is passed in, and `false` otherwise

      See Also:
      `setIncludeSynonyms`

    <!-- -->

    - #### getRestrictGetTables

          boolean getRestrictGetTables()

      Gets the restriction status of the returned data in `DatabaseMetaData.getTables`.
      The default behavior is to return information about all synonyms, including those which do not point to accessible tables or views. But you can change this with the `setRestrictGetTables` method.

      Returns:
      `true` if the information returned by `DatabaseMetaData.getTables` is restricted, and `false` otherwise

      See Also:
      `setRestrictGetTables`

    <!-- -->

    - #### getJavaObject

          Object getJavaObject(String sql_name)
                        throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getRemarksReporting

          boolean getRemarksReporting()

      Checks whether or not a call of `getTables` or `getColumns` of the `DatabaseMetaData` interface will report the `REMARKS` column.
      By default and for performance reasons it won't (it will return `null`) but you can change this with the `setRemarksReporting` method.

      Returns:
      `true` if the `DatabaseMetaData` calls `getTables` and `getColumns` will report the REMARKS column and `false` otherwise

      See Also:
      `setRemarksReporting`

    <!-- -->

    - #### getSQLType

          String getSQLType(Object obj)
                     throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getStmtCacheSize

          int getStmtCacheSize()

      Deprecated. Use getStatementCacheSize() instead.

    <!-- -->

    - #### getStructAttrCsId

          short getStructAttrCsId()
                           throws SQLException

      Obtain the Oracle identifier of the character set used in STRUCT attributes. Note that the network transport layer always send structure attributes in the database character set.
      Returns:
      the Oracle identifier of the character set.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if Conversion is `null`

      See Also:
      [oracle.sql.CharacterSet](../sql/CharacterSet.md) for the set of constants defined for the identifiers."

    <!-- -->

    - #### getUserName

          String getUserName()
                      throws SQLException

      Gets the user name of the current connection.
      Example where `conn` is your connection object:
      `String UserName = ((OracleConnection)conn).getUserName();`

      Returns:
      the user name

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the logical connection is closed

    <!-- -->

    - #### getCurrentSchema

          String getCurrentSchema()
                           throws SQLException

      Obtains the current schema of the current connection.
      Returns:
      current_schema value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If there was an error while fetching the results

    <!-- -->

    - #### getUsingXAFlag

          boolean getUsingXAFlag()

      Deprecated. 
      Gets the value of the `UsingXA` flag which the driver sets to `true` when using XA to manage distributed transactions. If you are not using distributed transactions with the XA library, the value of the `UsingXA` flag will be `false`.
      Returns:
      `true` when using XA to manage distributed transactions and `false` otherwise.

      See Also:
      `setUsingXAFlag`

    <!-- -->

    - #### getXAErrorFlag

          boolean getXAErrorFlag()

      Deprecated. 
      Gets the value of the `XAError` flag which is used with distributed transactions.
      When using distributed transactions with an XA library, you can ask the driver to raise exception when doing anything that might require a transaction. To do so, set the value of the `XAError` flag to `true` with the method `setXAErrorFlag`.

      The default value is `false`.

      Returns:
      `false` is the normal JDBC usage. `true` means that the driver will raise an exception when doing anything that might require a transaction.

      See Also:
      `setXAErrorFlag`

    <!-- -->

    - #### pingDatabase

          int pingDatabase()
                    throws SQLException

      Ping Database server to see if both database and the connection are actively up.
      Returns:
      DATABASE_OK if the database server is up, and DATABASE_CLOSED if any error occurs.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### pingDatabase

          int pingDatabase(int timeOut)
                    throws SQLException

      Deprecated. 
      ping Database
      Parameters:
      `timeOut` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### putDescriptor

          void putDescriptor(String sql_name,
                             Object desc)
                      throws SQLException

      Store the Object Descriptor for later usage.
      Parameters:
      `sql_name` - the sql type

      `desc` - the Object Descriptor associated

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if sql_name or desc is `null`

      See Also:
      `getDescriptor`, [`oracle.sql.TypeDescriptor`](../sql/TypeDescriptor.md)

    <!-- -->

    - #### registerSQLType

          void registerSQLType(String sql_name,
                               Class java_class)
                        throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### registerSQLType

          void registerSQLType(String sql_name,
                               String java_class_name)
                        throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setAutoClose

          void setAutoClose(boolean autoClose)
                     throws SQLException

      set auto-close mode. Only true is accepted.
      Parameters:
      `autoClose` - the boolean value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - when the argument autoClose is `false`

      See Also:
      `getAutoClose`

    <!-- -->

    - #### setDefaultExecuteBatch

          void setDefaultExecuteBatch(int batch)
                               throws SQLException

      Deprecated. As of 12.1 all APIs related to oracle-style statement batching are deprecated in favor of standard JDBC batching. We recommend using the standard model going forward as it is spec compliant and provides more information and control to the application.
      Executions are not batched but sent immediately. Oracle style of batching has been deprecated in 12.1 and made a no-op in 12.2. We recommend using the standard model of batching.
      Parameters:
      `batch` - value is discarded.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - never thrown.

      See Also:
      [`OraclePreparedStatement.setExecuteBatch`](OraclePreparedStatement.md), `getDefaultExecuteBatch`

    <!-- -->

    - #### setDefaultRowPrefetch

          void setDefaultRowPrefetch(int value)
                              throws SQLException

      Sets the value of row prefetch for all statements associated with this connection and created after this value was set.
      The row-prefetching feature associates an integer row-prefetch setting with a given statement object. JDBC fetches that number of rows at a time from the database during the query. That is, JDBC will fetch N rows that match the query criteria and bring them all back to the client at once, where N is the prefetch setting. Then, once your `next` calls have run through those N rows, JDBC will go back to fetch the next N rows that match the criteria.

      You can set the number of rows to prefetch for a particular Oracle statement (any type of statement) but this method allows you to reset the default number of rows that will be prefetched for all statements in your connection. The default number of rows to prefetch to the client is 10.

      Use the `setDefaultRowPrefetch` method to set the default number of rows to prefetch, passing in an integer that specifies the desired default. If you want to check the current setting of the default, then use the `getDefaultRowPrefetch` method. This method returns an integer.

      Example where `conn` is your connection object:
      `//Set the default row-prefetch setting for this connection to 7`
      `((OracleConnection)conn).setDefaultRowPrefetch(7);`

      Note 1 : A statement object receives the default row-prefetch setting from the associated connection at the time the statement object is created. Subsequent changes to the connection's default row-prefetch setting have no effect on the statement's row-prefetch setting.

      Note 2 : If a column of a result set is of datatype LONG or LONG RAW (that is, the streaming types), JDBC changes the statement's row-prefetch setting to 1, even if you never actually read a value of either of those types.

      Note 3 : Do not mix the JDBC 2.0 fetch size API and the Oracle row-prefetching API in your application. You can use one or the other but not both.

      Parameters:
      `value` - the number of rows to prefetch

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the argument `value` is \<=0

      See Also:
      [`OracleStatement.setRowPrefetch`](OracleStatement.md), `getDefaultRowPrefetch`

    <!-- -->

    - #### setEndToEndMetrics

          void setEndToEndMetrics(String[] metrics,
                                  short sequenceNumber)
                           throws SQLException

      Deprecated. It has been deprecated since 12.1 in favor of setClientInfo(). It is not recommended to use this API intermingled with get/setClientInfo APIs.
      Sets the values of the end-to-end tracing metrics. The indices for the array are the END_TO_END_XXX_INDEX values defined in this class. The values set by this method are overridden by any values set via DMS if DMS is in use.
      Parameters:
      `metrics` - String\[\] containing the metric values.

      `sequenceNumber` - the sequence number for the context id

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      See Also:
      `getEndToEndMetrics`, [`Connection.setClientInfo(java.util.Properties)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setClientInfo_java_util_Properties_), [`Connection.setClientInfo(java.lang.String, java.lang.String)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setClientInfo_java_lang_String_java_lang_String_)

    <!-- -->

    - #### setIncludeSynonyms

          void setIncludeSynonyms(boolean synonyms)

      Turns on or off retrieval of synonym information in DatabaseMetaData. getColumns.
      Similar to `setRemarksReporting`, `getColumns` performs extremely slow if information about synonyms has to be included, because it neccessitates an outer join so, by default, the JDBC driver will not report information about synonyms.

      You can get synonym information by passing true to this method, and turn it off by passing false. You can also control this behavior by passing a property named "includeSynonyms" as "true" to DriverManager.getConnection.

      Parameters:
      `synonyms` - `true` if you want to retrieve synonym information in DatabaseMetaData.getColumns and `false` otherwise.

      See Also:
      `getIncludeSynonyms`

    <!-- -->

    - #### setRemarksReporting

          void setRemarksReporting(boolean reportRemarks)

      Turns on or off the reporting of the REMARKS columns by the `getTables` and `getColumns` calls of the `DatabaseMetaData` interface.
      The `DatabaseMetaData` calls `getTables` and `getColumns` are extremely slow if the REMARKS column has to be reported as this necessitates an expensive outer join so by default the JDBC driver does not report the REMARKS columns.

      You can turn the reporting of REMARKS on by passing a `true` argument to this method. You turn it back off by passing a `false` argument.

      Example where `conn` is your connection object:
      `((OracleConnection)conn).setRemarksReporting(true);`

      You can also control the reporting of REMARKS by passing a property named `remarksReporting` as `true` to the `DriverManager.getConnection` call.

      Parameters:
      `reportRemarks` - `true` if you want to turn on the reporting of the REMARKS columns and `false` otherwise.

      See Also:
      `getRemarksReporting`

    <!-- -->

    - #### setRestrictGetTables

          void setRestrictGetTables(boolean restrict)

      Turns on or off the restriction of the returned data in `DatabaseMetaData.getTables.`
      `DatabaseMetaData.getTables` will return information about all accessible tables, views, and synonyms. There are two issues relating to synonyms which can affect the quality of the returned data:

      1.  Public synonyms can exist for tables to which you don't have access. Although the synonym itself is viewable, the underlying table is not.
      2.  Synonyms can exist for non-table objects, such as procedures, sequences, Java classes, etc.

      As a result of the above issues, `getTables` can return rows containing objects that are not describable with `getColumns`, either because they are not accessible (issue 1) or because they are not tables or views (issue 2).
      To remedy this, you can restrict the results of `getTables` to only those tables and views to which you have access. This is done by either passing `true` to this method, or by passing the `restrictGetTables` property as `true` to the `DriverManager.getConnection` call. The default behavior is to return information about all synonyms, including those which do not point to accessible tables or views.

      Note that `getTables` can return more than one row for the same object, one for the object itself, and additional rows for any synonyms defined for that object. This is the case regardless of the setting for `restrictGetTables.`

      The following code turns on the restriction:
      `((OracleConnection)conn).setRestrictGetTables(true);`

      Parameters:
      `restrict` - `true` to turn on the restriction and `false` otherwise.

      See Also:
      `getRestrictGetTables`

    <!-- -->

    - #### setStmtCacheSize

          void setStmtCacheSize(int size)
                         throws SQLException

      Deprecated. Use setStatementCacheSize() instead.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setStmtCacheSize

          void setStmtCacheSize(int size,
                                boolean clearMetaData)
                         throws SQLException

      Deprecated. Use setStatementCacheSize() instead.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setStatementCacheSize

          void setStatementCacheSize(int size)
                              throws SQLException

      setStatementCacheSize Specifies the size of the size of the application cache (which will be used by both implicit and explicit caching).
      Parameters:
      `size` - Requested size of the cache. If the existing cache size is less than size, statements will be purged to reduce the size.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if size \< 0, or if called on a logical connection.

    <!-- -->

    - #### getStatementCacheSize

          int getStatementCacheSize()
                             throws SQLException

      getStatementCacheSize Returns the current size of the application cache. This is valid on both physical and logical connections. If the statement cache has not been initialized with setStatementCacheSize(), then CACHE_SIZE_NOT_SET is returned.
      Returns:
      the cache size

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setImplicitCachingEnabled

          void setImplicitCachingEnabled(boolean cache)
                                  throws SQLException

      setImplicitCachingEnabled Enables or disables the implicit cache. Note that this is independent of the cache size, set with setStatmentCacheSize().
      Parameters:
      `cache` - If true, then implicit caching will be enabled. If false, then any existing statements will be purged and the implicit cache will be disabled.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if called on a logical connection.

    <!-- -->

    - #### getImplicitCachingEnabled

          boolean getImplicitCachingEnabled()
                                     throws SQLException

      getImplicitCachingEnabled Returns true if the implicit cache is currently enabled, false otherwise. This method is valid on both logical and physical connections.
      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setExplicitCachingEnabled

          void setExplicitCachingEnabled(boolean cache)
                                  throws SQLException

      setExplicitCachingEnabled Enables or disables the explicit cache. Note that this is independent of the cache size, set with setStatmentCacheSize().
      Parameters:
      `cache` - If true, then explicit caching will be enabled. If false, then any existing statements will be purged and the explicit cache will be disabled.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if called on a logical connection.

    <!-- -->

    - #### getExplicitCachingEnabled

          boolean getExplicitCachingEnabled()
                                     throws SQLException

      getExplicitCachingEnabled Returns true if the explicit cache is currently enabled, false otherwise. This method is valid on both logical and physical connections.
      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### purgeImplicitCache

          void purgeImplicitCache()
                           throws SQLException

      purgeImplicitCache Removes all existing statements from the implicit cache, after which it will be empty. This method does not affect the size of the application cache, nor the enabled/disabled status.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### purgeExplicitCache

          void purgeExplicitCache()
                           throws SQLException

      purgeExplicitCache Removes all existing statements from the explicit cache, after which it will be empty. This method does not affect the size of the application cache, nor the enabled/disabled status.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getStatementWithKey

          PreparedStatement getStatementWithKey(String key)
                                         throws SQLException

      getStatementWithKey Searches the explicit cache for a match on key. If found, the statement is returned, with the paramater and define metadata identical to the last usage. If no match is found, or if explicit caching is not enabled, then null is returned (as opposed to throwing an exception).
      Parameters:
      `key` - Specified key to search for

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getCallWithKey

          CallableStatement getCallWithKey(String key)
                                    throws SQLException

      getCallWithKey Searches the explicit cache for a match on key. If found, the statement is returned, with the paramater and define metadata identical to the last usage. If no match is found, or if explicit caching is not enabled, then null is returned (as opposed to throwing an exception).
      Parameters:
      `key` - Specified key to search for

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setUsingXAFlag

          void setUsingXAFlag(boolean value)

      Deprecated. 
      When using distributed transactions with XA, you can set the value of the `UsingXA` flag.
      XA is a general standard (not specific to Java) for distributed transactions. You should use this method only when using XA.

      By default, when using distributed transactions with XA, the driver will set the `UsingXA` flag to `true` and exceptions will be raised when you want to do anything with your logical connection that might require a transaction. Otherwise the flag `UsingXA` is always `false`.

      If you are actually using distributed transactions with XA and you dislike the default behavior, you can set the flag back to `false`.

      Parameters:
      `value` - the value of the `UsingXA` flag

      See Also:
      `getUsingXAFlag`

    <!-- -->

    - #### setXAErrorFlag

          void setXAErrorFlag(boolean value)

      Deprecated. 
      Sets the value of the `XAError` flag which is used with distributed transactions. When coexisting with an XA library, you can set the `XAError` flag to `true` and the driver will then raise an exception when doing anything that might require a transaction.
      Parameters:
      `value` - the value of the `XAError` flag

      See Also:
      `getXAErrorFlag`

    <!-- -->

    - #### shutdown

          void shutdown(OracleConnection.DatabaseShutdownMode mode)
                 throws SQLException

      Shuts the database server down. This method requires to be connected as either SYSOPER or SYSDBA.
      Parameters:
      `mode` - can be either

      - `OracleConnection.DatabaseShutdownMode.CONNECT`
      - `OracleConnection.DatabaseShutdownMode.TRANSACTIONAL`
      - `OracleConnection.DatabaseShutdownMode.TRANSACTIONAL_LOCAL`
      - `OracleConnection.DatabaseShutdownMode.IMMEDIATE`
      - `OracleConnection.DatabaseShutdownMode.ABORT`
      - `OracleConnection.DatabaseShutdownMode.FINAL`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### startup

          void startup(String startup_str,
                       int mode)
                throws SQLException

      Deprecated. This method will be removed in a future version.
      Not implemented
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### startup

          void startup(OracleConnection.DatabaseStartupMode mode)
                throws SQLException

      Starts the database server up. This method requires to be connected as either SYSOPER or SYSDBA in the PRELIM_AUTH mode which is the only mode permietted when the database is down (see the connection property CONNECTION_PROPERTY_PRELIM_AUTH).
      Parameters:
      `mode` - can be either

      - `OracleConnection.DatabaseStartupMode.NO_RESTRICTION`
      - `OracleConnection.DatabaseStartupMode.FORCE`
      - `OracleConnection.DatabaseStartupMode.RESTRICT`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### startup

          void startup(OracleConnection.DatabaseStartupMode mode,
                       String pfileName)
                throws SQLException

      Starts the database server up. This method requires to be connected as either SYSOPER or SYSDBA in the PRELIM_AUTH mode which is the only mode permietted when the database is down (see the connection property CONNECTION_PROPERTY_PRELIM_AUTH).
      Parameters:
      `mode` - can be either

      - `OracleConnection.DatabaseStartupMode.NO_RESTRICTION`
      - `OracleConnection.DatabaseStartupMode.FORCE`
      - `OracleConnection.DatabaseStartupMode.RESTRICT`

      `pfileName:` - PFILE name. If client-side parameter file is null or doesn't exist, it will throw exception otherwise read the file and pass parameters to server.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### prepareStatementWithKey

          PreparedStatement prepareStatementWithKey(String key)
                                             throws SQLException

      Deprecated. This is same as prepareStatement, except if a Prepared Statement with the given KEY exists in the Cache, then the statement is returned AS IT IS when it was closed and cached with this KEY. An object returned from the Cache based on Key will have its state set to "KEYED". If no such Prepared Statement is found, a null is returned. Key cannot be null.
      Parameters:
      `key` - the key with which it was closed

      Returns:
      a OraclePreparedStatement object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### prepareCallWithKey

          CallableStatement prepareCallWithKey(String key)
                                        throws SQLException

      Deprecated. This is same as prepareCall, except if a Callable Statement with the given KEY exists in the Cache, then the statement is returned AS IT IS when it was closed and cached with this KEY. An object returned from the Cache based on Key will have its state set to "KEYED". If no such Callable Statement is found, then null is returned. Key cannot be null.
      Parameters:
      `key` - the key with which it was closed

      Returns:
      a java.sql.CallableStatement object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setCreateStatementAsRefCursor

          void setCreateStatementAsRefCursor(boolean value)

      When this is set to `true`, any new statements created from this connection will be created as a `REF CURSOR`. Only resultsets obtained from statements that are created as `REF CURSORS` can be returned from a Java Stored Procedure. This feature is supported by the server-side internal driver only, and is no-op in all other JDBC drivers.
      Default value is `false`.

      To use the `setCreateStatementAsRefCursor` entrypoint you have to cast the Connection object to the type `oracle.jdbc.OracleConnection`.

      Parameters:
      `value` - `true` if new statements should be created as `REF CURSORS`, `false` otherwise

      See Also:
      `getCreateStatementAsRefCursor`

    <!-- -->

    - #### getCreateStatementAsRefCursor

          boolean getCreateStatementAsRefCursor()

      Retrieves the current setting of the `createStatementAsRefCursor` flag which you can set with the `setCreateStatementAsRefCursor` method.
      To use the `getCreateStatementAsRefCursor` entrypoint you have to cast the Connection object to the type `oracle.jdbc.OracleConnection`.

      Returns:
      the current setting of the createStatementAsRefCursor flag

      See Also:
      `setCreateStatementAsRefCursor`

    <!-- -->

    - #### setSessionTimeZone

          void setSessionTimeZone(String regionName)
                           throws SQLException

      Set the session time zone.
      This method is used to set the session time zone. This method must be invoked before accessing any TIMESTAMP WITH LOCAL TIME ZONE data. Upon invocation of this method, the Jdbc driver sets the session timezone of the connection and saves the session timezone so that any TSLTZ data accessed via Jdbc are adjusted using the session timezone.

      Parameters:
      `regionName` - Oracle session time zone region name.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurred.

      Since:
      9i

    <!-- -->

    - #### getSessionTimeZone

          String getSessionTimeZone()

      Obtain Oracle session time zone region name.
      Returns:
      Oracle session time zone region name.

      Since:
      9i

    <!-- -->

    - #### getSessionTimeZoneOffset

          String getSessionTimeZoneOffset()
                                   throws SQLException

      Obtain the time zone offset in hours of the current database session. The result will always be accurate. In other words, you can execute `"ALTER SESSION SET TIME_ZONE ..."` and then call this method, it will return the new value.
      The value returned by this method is that same as the result of `"SELECT SESSIONTIMEZONE FROM DUAL;"`. The drivers may use some performance optimization to not use a roundtrip to the server so it is always preferrable to use this method.

      Returns:
      Oracle session time zone in hours. For example "-7:00" or "0:00"

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.1

    <!-- -->

    - #### getProperties

          Properties getProperties()

      Determines the connection properties.
      Returns:

    <!-- -->

    - #### \_getPC

          Connection _getPC()

      Return the underlying physical connection if this is a logical connection. Returns null otherwise.
      Returns:
      Connection object if its a logical handle otherwise returns null

    <!-- -->

    - #### isLogicalConnection

          boolean isLogicalConnection()

      Method that returns a boolean indicating whether its a logical connection or not.
      Returns:
      boolean true if this is a logical connection

    <!-- -->

    - #### registerTAFCallback

          void registerTAFCallback(OracleOCIFailover cbk,
                                   Object obj)
                            throws SQLException

      Register an application TAF Callback instance that will be called when an application failover occurs. The TAF feature is only available in the Jdbc OCI driver.
      Parameters:
      `cbk` - Callback instance.

      `obj` - Context object in which any client's state can be stored and provided when the callback method is invoked.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if this method is invoked in drivers other than the Jdbc OCI driver.

      Since:
      9i

    <!-- -->

    - #### unwrap

          OracleConnection unwrap()

      Return the wrapped object if any else null. This method should not delegate to the wrapped object. Instead it should return the wrapped object.
      Returns:
      wrapped object which implements oracle.jdbc.OracleConnection if any else return null

      Since:
      9iRw

    <!-- -->

    - #### setWrapper

          void setWrapper(OracleConnection wrapper)

      Set the wrapping object. The argument is an object that wraps this object. Calling wrapper.unwrap() should return this.
      Parameters:
      `wrapper` - An object which implements oracle.jdbc.OracleConnection and which is a wrapper for this object \# @since 9iR2

    <!-- -->

    - #### oracleSetSavepoint

          OracleSavepoint oracleSetSavepoint()
                                      throws SQLException

      Creates an unnamed savepoint in the current transaction and returns the new `OracleSavepoint` object that represents it.
      Returns:
      the new `OracleSavepoint` object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs or this `Connection` object is currently in auto-commit mode

      Since:
      9.0.2

      See Also:
      [`OracleSavepoint`](OracleSavepoint.md)

    <!-- -->

    - #### oracleSetSavepoint

          OracleSavepoint oracleSetSavepoint(String name)
                                      throws SQLException

      Creates a savepoint with the given name in the current transaction and returns the new `OracleSavepoint` object that represents it.
      Parameters:
      `name` - a `String` containing the name of the savepoint

      Returns:
      the new `OracleSavepoint` object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs or this `Connection` object is currently in auto-commit mode

      Since:
      9.0.2

      See Also:
      [`OracleSavepoint`](OracleSavepoint.md)

    <!-- -->

    - #### oracleRollback

          void oracleRollback(OracleSavepoint savepoint)
                       throws SQLException

      Undoes all changes made after the given `OracleSavepoint` object was set.
      This method should be used only when auto-commit has been disabled.

      Parameters:
      `savepoint` - the `OracleSavepoint` object to roll back to

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs, the `OracleSavepoint` object is no longer valid, or this `Connection` object is currently in auto-commit mode

      Since:
      9.0.2

      See Also:
      [`OracleSavepoint`](OracleSavepoint.md)

    <!-- -->

    - #### oracleReleaseSavepoint

          void oracleReleaseSavepoint(OracleSavepoint savepoint)
                               throws SQLException

      Removes the given `OracleSavepoint` object from the current transaction. Any reference to the savepoint after it have been removed will cause an `SQLException` to be thrown.
      Parameters:
      `savepoint` - the `OracleSavepoint` object to be removed

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs or the given `OracleSavepoint` object is not a valid savepoint in the current transaction

      Since:
      9.0.2

      See Also:
      [`OracleSavepoint`](OracleSavepoint.md)

    <!-- -->

    - #### close

          void close(Properties connAttr)
              throws SQLException

      Closes the given Logical connection, and returns the underlying PooledConnection to the implicit connection cache. The connection Attributes is set on the PooledConnection. If the connection Attributes passed is null, then a null value is set on the PooledConnection as well. When called on a physical connection, the connection Attributes passed in has no effect.
      Parameters:
      `connAttr` - the connection Attributes to be applied

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### close

          void close(int opt)
              throws SQLException

      If opt is OracleConnection.INVALID_CONNECTION : Closes the given Logical connection, as well the underlying PooledConnection without returning the connection to the cache when called with the parameter INVALID_CONNECTION. If this API is called on a physical connection, the supplied parameter has no effect.

      If opt is OracleConnection.PROXY_SESSION : Closes the proxy session (opened with openProxySession()).
      Parameters:
      `opt` - set to INVALID_CONNECTION to close the PooledConnection

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### isProxySession

          boolean isProxySession()

      Returns true if the current session associated with this connection is a proxy session.
      Returns:

    <!-- -->

    - #### applyConnectionAttributes

          void applyConnectionAttributes(Properties connAttr)
                                  throws SQLException

      Applies the connection Attributes provided on the underlying PooledConnection. The connection Attributes set via the close API overrides the value set by this API.
      Parameters:
      `connAttr` - the connection Attributes to be applied

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### getConnectionAttributes

          Properties getConnectionAttributes()
                                      throws SQLException

      Returns the connection Attributes set on the underlying PooledConnection. This API returns null when called on a physical connection.
      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### getUnMatchedConnectionAttributes

          Properties getUnMatchedConnectionAttributes()
                                               throws SQLException

      Returns the unmatched connection Attributes from the underlying PooledConnection. These are essentially the PooledConnection Attributes that did not match the ones from the connection request. This API returns null when called on a physical connection.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### registerConnectionCacheCallback

          void registerConnectionCacheCallback(OracleConnectionCacheCallback occc,
                                               Object userObj,
                                               int cbkFlag)
                                        throws SQLException

      Registers the connection cache callback on the logical connection This is used in conjunction with the Implicit Connection Cache Properties.
      Parameters:
      `occc` - Implementation of the OracleConnectionCacheCallback Interface

      `userObj` - User private object to be passed when invoking callbacks

      `cbkFlag` - Indicates which callback method to invoke. Supported values are: ABANDONED_CONNECTION_CALLBACK RELEASE_CONNECTION_CALLBACK ALL_CONNECTION_CALLBACKS

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setConnectionReleasePriority

          void setConnectionReleasePriority(int priority)
                                     throws SQLException

      Sets connection release priority. Works in conjunction with the Connection Cache Callback method RELEASE_CONNECTION_CALLBACK Suported release priorities are: CONNECTION_RELEASE_LOCKED CONNECTION_RELEASE_LOW CONNECTION_RELEASE_HIGH
      Parameters:
      `priority` - one of the above release priority

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### getConnectionReleasePriority

          int getConnectionReleasePriority()
                                    throws SQLException

      Returns the release priority set on the connection
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setPlsqlWarnings

          void setPlsqlWarnings(String setting)
                         throws SQLException

      Enable/Disable PLSQL Compiler Warnings
      Parameters:
      `setting` - Setting specified for ALTER SESSION SET PLSQL_WARNINGS. Sample values are: "'ENABLE:ALL'", "'DISABLE:ALL'", "'ENALBLE:INFORMATIONAL'", etc. Please refer to the SQL reference of ALTER SESSION SET PLSQL_WARNINGS for more information. If the setting is "'DISABLE:ALL'", jdbc drivers turn off PLSQL Compiler Warnings. Note: the quotes(') in the setting String are necessary.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### registerAQNotification

          AQNotificationRegistration[] registerAQNotification(String[] name,
                                                              Properties[] options,
                                                              Properties globaloptions)
                                                       throws SQLException

      Registers your interest into being notified when a message is enqueued in a particular queue (or array of queues).
      This method creates an array of new AQ registrations in the database server with the given options. It also opens a listening socket which will be used by the database to send notifications. Note that mutiple registrations can share the same listening socket.

      Each registration will continue to live after this connection is closed. You need to explicitly unregister it to destroy it in the server and release the resources in the driver.

      This method uses one roundtrip.

      Parameters:
      `name` - contains an array of queue names ("SCOTT.MY_QUEUE") for single consumer queues or queue names with the consumer name ("SCOTT.MY_QUEUE:RECEIVER") for multiple consumer queues.

      `options` - Possible options are (\[\] means default):

      - `OracleConnection.NTF_QOS_RELIABLE`: "true"/\["false"\]. Set this option to "true" to make the notifications persistent which comes at a performance cost.
      - `OracleConnection.NTF_QOS_PURGE_ON_NTFN`: "true"/\["false"\]. Set this option to "true" and the registration will be expunged on the first notification event.
      - `OracleConnection.NTF_TIMEOUT`: value in seconds "60"/\["0"\]. Specifies the time in seconds after which the registration is automatically expunged by the database. The default is "0": the registration lives until explicitly deregistered.
      - `OracleConnection.NTF_AQ_PAYLOAD`: "true"/\["false"\]. Sets this to "true" to make the server send the payload within the notification. Note that this feature works only with "RAW" payloads.
      - `OracleConnection.NTF_GROUPING_CLASS`: `OracleConnection.NTF_GROUPING_CLASS_TIME`/\[`OracleConnection.NTF_GROUPING_CLASS_NONE`\]. Notification Grouping Class, the criterion or dimension for grouping. As of 11.2 the only supported class is `OracleConnection.NTF_GROUPING_CLASS_TIME` meaning grouping by time, that is, the user specifies a time value and a single notification gets published at the end of that time. To use grouping at least this option must be specified to a value other than the default `OracleConnection.NTF_GROUPING_CLASS_NONE`, which is no grouping.
      - `OracleConnection.NTF_GROUPING_VALUE`: "1200/\["600"\]. Notification Grouping Value, the value of the grouping class. The value must be an integer number. For the TIME grouping class, this value represents a number of seconds, meaning the time after which grouped notifications are sent. If not specified, it defaults to 600 sec.
      - `OracleConnection.NTF_GROUPING_TYPE`: `OracleConnection.NTF_GROUPING_TYPE_LAST`/\[`OracleConnection.NTF_GROUPING_TYPE_SUMMARY`\]. Notification Grouping Type, the format of grouping notification. It can either contain the summary of all events (default) or the last event in the group.
      - `OracleConnection.NTF_GROUPING_START_TIME`: When to start grouping? Notification grouping can start from a user-specified time that should a valid timestamp with time zone, that is an instance of `oracle.sql.TIMESTAMPTZ`. If this option is not specified when using grouping, it defaults to current system time. For example if `prop` was the option properties, and `conn` the connection object, you would call: `prop.put(OracleConnection.NTF_GROUPING_START_TIME,new TIMESTAMPTZ(conn,"2007-06-21 10:10:00.0"));`.
      - `OracleConnection.NTF_GROUPING_REPEAT_TIME`: "100/\[`NTF_GROUPING_REPEAT_FOREVER`\]". How many times do grouping? Grouping notifications will be sent as many times as specified by the notification grouping repeat count and after that revert to regular notifications. If not specified, it will default to: `NTF_GROUPING_REPEAT_FOREVER` - keep sending grouping notifications forever.

      `globaloptions` - Possible options are (\[\] means default):

      - `OracleConnection.NTF_LOCAL_TCP_PORT`: "1234"/\[NTF_DEFAULT_TCP_PORT\]. This option lets you specify what TCP port the driver should use for the listening socket. If you don't specify a port, the driver will use NTF_DEFAULT_TCP_PORT and if it's already used, it will increment it by one until it finds one that is available.
      - `OracleConnection.NTF_LOCAL_HOST`: example "212.121.134.12". Use this option to manually specify the IP address of the machine that will receive the notifications from the server. Use this option with caution: only specify the IP address of the local machine when the driver is unable to find it out on its own (it uses `InetAddress.getLocalHost()` ). For example if the machine on which runs the JDBC driver is a VPN client, you may have to specify the IP address of the VPN client which the driver cannot find out on its own. This option should **not** be used to attempt to have a different remote host receive the notifications from the server.

      Returns:
      AQNotificationRegistration\[\]

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.1

    <!-- -->

    - #### unregisterAQNotification

          void unregisterAQNotification(AQNotificationRegistration registration)
                                 throws SQLException

      Deletes a given AQ registration. The registration will be destroyed in the server and in the driver (the network listener will be closed if it's not used anymore).
      Parameters:
      `registration` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.1

    <!-- -->

    - #### dequeue

          AQMessage dequeue(String queueName,
                            AQDequeueOptions opt,
                            byte[] tdo)
                     throws SQLException

      Dequeues an AQ message from the queue specified by its name.
      Parameters:
      `queueName` - name of the queue from which to dequeue.

      `opt` - dequeue options

      `tdo` - the Type Descriptor Object OID of the type of the queue.

      Returns:
      the AQMessage dequeued.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.1

    <!-- -->

    - #### dequeue

          AQMessage dequeue(String queueName,
                            AQDequeueOptions opt,
                            byte[] tdo,
                            int version)
                     throws SQLException

      Dequeues an AQ message from the queue specified by its name.
      Parameters:
      `queueName` - name of the queue from which to dequeue.

      `opt` - dequeue options

      `tdo` - the Type Descriptor Object OID of the type of the queue.

      `version` - the version of the type Descriptor

      Returns:
      the AQMessage dequeued.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.1

    <!-- -->

    - #### dequeue

          AQMessage dequeue(String queueName,
                            AQDequeueOptions opt,
                            String typeName)
                     throws SQLException

      Dequeues an AQ message from the queue specified by its name.
      Parameters:
      `queueName` - name of the queue from which to dequeue.

      `opt` - dequeue options.

      `typeName` - the name of the type of the queue. For example, it can be "RAW", "SYS.ANYDATA" or "SCOTT.MY_OBJECT_TYPE".

      Returns:
      the AQMessage dequeued.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.1

    <!-- -->

    - #### enqueue

          void enqueue(String queueName,
                       AQEnqueueOptions opt,
                       AQMessage mesg)
                throws SQLException

      Enqueues the given AQ message to the queue specified by its name.
      Parameters:
      `queueName` - name of the queue where to enqueue.

      `opt` - enqueue options.

      `mesg` - the AQ message to enqueue.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.1

    <!-- -->

    - #### registerDatabaseChangeNotification

          DatabaseChangeRegistration registerDatabaseChangeNotification(Properties options)
                                                                 throws SQLException

      Creates a new database change registration.
      This method creates a new database change registration in the database server with the given options. It also opens a listening socket which will be used by the database to send notifications. Note that if there already is a listening socket (created by a different registration), then it will be used by this registration as well.

      This method returns a DatabaseChangeRegistration object that can then be used to associate a statement with this registration.

      The registration will continue to live after this connection is closed. You need to explicitly unregister it to destroy it in the server and release the resources in the driver.

      This method uses one roundtrip.

      Parameters:
      `options` - Possible options are (\[\] means default):

      - `OracleConnection.NTF_QOS_RELIABLE`: "true"/\["false"\]. Set this option to "true" to make the notifications persistent which comes at a performance cost.
      - `OracleConnection.NTF_QOS_PURGE_ON_NTFN`: "true"/\["false"\]. Set this option to "true" and the registration will be expunged on the first notification event.
      - `OracleConnection.NTF_TIMEOUT`: value in seconds "60"/\["0"\]. Specifies the time in seconds after which the registration is automatically expunged by the database. The default is "0": the registration lives until explicitly deregistered.
      - `OracleConnection.NTF_LOCAL_TCP_PORT`: "1234"/\[NTF_DEFAULT_TCP_PORT\]. This option lets you specify what TCP port the driver should use for the listening socket. If you don't specify a port, the driver will use NTF_DEFAULT_TCP_PORT and if it's already used, it will increment it by one until it finds one that is available.
      - `OracleConnection.NTF_LOCAL_HOST`: example "212.121.134.12". Use this option to manually specify the IP address of the machine that will receive the notifications from the server. Use this option with caution: only specify the IP address of the local machine when the driver is unable to find it out on its own (it uses `InetAddress.getLocalHost()` ). For example if the machine on which runs the JDBC driver is a VPN client, you may have to specify the IP address of the VPN client which the driver cannot find out on its own. This option should **not** be used to attempt to have a different remote host receive the notifications from the server.
      - `OracleConnection.DCN_NOTIFY_ROWIDS`: "true"/\["false"\]. Use this option to have the server send the ROWIDs of the row that have changed within the notification event. By default this feature is turned off.
      - `OracleConnection.DCN_IGNORE_INSERTOP`: "true"/\["false"\]. Use this option to tell the server to ignore INSERT operations.
      - `OracleConnection.DCN_IGNORE_UPDATEOP`: "true"/\["false"\]. Use this options to tell the server to ignore UPDATE operations.
      - `OracleConnection.DCN_IGNORE_DELETEOP`: "true"/\["false"\]. Use this options to tell the server to ignore DELETE operations.
      - `OracleConnection.DCN_NOTIFY_CHANGELAG`: "30"/\["0"\]. This is an int value (specified as a String), that can be used to specify the number of transactions by which the client is willing to lag behind. This option can be used by the client as a throttling mechanism for database change events. When this option is chosen, ROWID level granularity of information will not be available in the events, even if the DCN_NOTIFY_ROWIDS option was set to "true".
      - `OracleConnection.DCN_QUERY_CHANGE_NOTIFICATION`: "true"/\["false"\]. Use this option to activate query change notification instead of object change notification. Note that this option is only available in the database server starting in 11.1.
      - `OracleConnection.DCN_BEST_EFFORT`: "true"/\["false"\]. If a query has been successfully registered, by default there will be no FALSE positives. If this option is selected during registrations, then registrations on complex queries may still be allowed but notifications may have some FALSE positives, because full pruning may not be performed if determined to be too expensive. In the worst case notifications will be generated in response to any DML/DDL changes to underlying objects. Note that this option is ignored if the `DCN_QUERY_CHANGE_NOTIFICATION` isn't turned on. As `DCN_QUERY_CHANGE_NOTIFICATION`, this option is only available in the database server starting in 11.1.
      - `OracleConnection.NTF_GROUPING_CLASS`: `OracleConnection.NTF_GROUPING_CLASS_TIME`/\[`OracleConnection.NTF_GROUPING_CLASS_NONE`\]. Notification Grouping Class, the criterion or dimension for grouping. The only supported class is `OracleConnection.NTF_GROUPING_CLASS_TIME` meaning grouping by time, that is, the user specifies a time value and a single notification gets published at the end of that time. To use grouping at least this option must be specified to a value other than the default `OracleConnection.NTF_GROUPING_CLASS_NONE`, which is no grouping.
      - `OracleConnection.NTF_GROUPING_VALUE`: "1200/\["600"\]. Notification Grouping Value, the value of the grouping class. The value must be an integer number. For the TIME grouping class, this value represents a number of seconds, meaning the time after which grouped notifications are sent. If not specified, it defaults to 600 sec.
      - `OracleConnection.NTF_GROUPING_TYPE`: `OracleConnection.NTF_GROUPING_TYPE_LAST`/\[`OracleConnection.NTF_GROUPING_TYPE_SUMMARY`\]. Notification Grouping Type, the format of grouping notification. It can either contain the summary of all events (default) or the last event in the group.
      - `OracleConnection.NTF_GROUPING_START_TIME`: When to start grouping? Notification grouping can start from a user-specified time that should a valid timestamp with time zone, that is an instance of `oracle.sql.TIMESTAMPTZ`. If this option is not specified when using grouping, it defaults to current system time. For example if `prop` was the option properties, and `conn` the connection object, you would call: `prop.put(OracleConnection.NTF_GROUPING_START_TIME,new TIMESTAMPTZ(conn,"2007-06-21 10:10:00.0"));`.
      - `OracleConnection.NTF_GROUPING_REPEAT_TIME`: "100"/\[`NTF_GROUPING_REPEAT_FOREVER`\]. How many times do grouping? Grouping notifications will be sent as many times as specified by the notification grouping repeat count and after that revert to regular notifications. If not specified, it will default to: `NTF_GROUPING_REPEAT_FOREVER` - keep sending grouping notifications forever.
      - `OracleConnection.DCN_CLIENT_INIT_CONNECTION`: "true"/\["false"\]. This can be configured to initiate a connection from the client instead of opening a listener socket for receiving the database change notifications. Set the value to 'true' for using the Client initiated DCN connection. By default the value is 'false' and opens a listening socket for receiving notifications from the server.
      - `OracleConnection.DCN_USE_HOST_CONNECTION_ADDR_INFO`: \["true"\]/"false". Set the value to 'false' to use the address info returned by the server for establishing the client initiated DCN Connection. Default value is 'true' and the database hostname and port information present in this database connection's connection string is used for establishing the client initiated DCN connection.

      Returns:
      DatabaseChangeRegistration

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.1

    <!-- -->

    - #### getDatabaseChangeRegistration

          DatabaseChangeRegistration getDatabaseChangeRegistration(int regid)
                                                            throws SQLException

      Maps an existing registration identified by its ID 'regid' with a new DatabaseChangeRegistration object.
      This method can be used if you create a registration through PLSQL and you want to associate a JDBC statement with it.

      This method doesn't create a new listener on the JDBC driver side and DatabaseChangeEvent won't be created. Thus you won't be allowed to attach any listeners to this registration.

      Note that this method doesn't generate any roundtrip to the database.

      Parameters:
      `regid` - The id of the registration

      Returns:
      DatabaseChangeRegistration A new instance that can be used to associate a statement with this registration

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.1

    <!-- -->

    - #### unregisterDatabaseChangeNotification

          void unregisterDatabaseChangeNotification(DatabaseChangeRegistration registration)
                                             throws SQLException

      Deletes a given database change registration. The registration will be destroyed in the server and in the driver (the network listener will be closed if it's not used anymore).
      This method interrupts the notification thread and removes all listeners attached to this registration before closing it.

      Parameters:
      `registration` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.1

      See Also:
      `unregisterDatabaseChangeNotification(long,String)`

    <!-- -->

    - #### unregisterDatabaseChangeNotification

          void unregisterDatabaseChangeNotification(int registrationId,
                                                    String host,
                                                    int tcpport)
                                             throws SQLException

      Deprecated. 
      Deletes a given database change registration in the server. This method doesn't free any resources in the drivers.
      This method will throw an "ORA-24950: unregister failed, registration not found" if you don't provide the correct TCP port which can be extracted from the "callback" value in the "USER_CHANGE_NOTIFICATION_REGS" table.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.1

      See Also:
      `unregisterDatabaseChangeNotification(long,String)`

    <!-- -->

    - #### unregisterDatabaseChangeNotification

          void unregisterDatabaseChangeNotification(int registrationId)
                                             throws SQLException

      Deprecated. 
      Deletes a given database change registration in the server. This method doesn't free any resources in the drivers.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.1

      See Also:
      `unregisterDatabaseChangeNotification(long, String)`

    <!-- -->

    - #### unregisterDatabaseChangeNotification

          void unregisterDatabaseChangeNotification(long registrationId,
                                                    String callback)
                                             throws SQLException

      Deletes a given database change registration in the server. This method doesn't free any resources in the drivers and should only be used to clean up a registration in the database that wasn't properly closed (in the case of JVM crash for example).
      This flavor of `unregisterDatabaseChangeNotification` can be used to process the result of the following query: `select regid,callback from USER_CHANGE_NOTIFICATION_REGS;`.

      For example to remove all registrations from the database you would execute the following code:

              Statement stmt= conn.createStatement();
              ResultSet rs = stmt.executeQuery("select regid,callback from USER_CHANGE_NOTIFICATION_REGS");
              while(rs.next())
              {
                long regid = rs.getLong(1);
                String callback = rs.getString(2);
                ((OracleConnection)conn).unregisterDatabaseChangeNotification(regid,callback);
              }
              rs.close();
              stmt.close();


      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `unregisterDatabaseChangeNotification(oracle.jdbc.dcn.DatabaseChangeRegistration)`

    <!-- -->

    - #### createARRAY

          ARRAY createARRAY(String typeName,
                            Object elements)
                     throws SQLException

      Creates an ARRAY object with the given type name and elements.
      Parameters:
      `typeName` - the name of the SQL type of the created object

      `elements` - the elements of the created object

      Returns:
      an ARRAY

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createOracleArray

          Array createOracleArray(String arrayTypeName,
                                  Object elements)
                           throws SQLException

      Creates an Array object with the given type name and elements. The standard createArrayOf accepts the element type name. This method accepts the type of the array itself. Oracle does not support anonymous array types and so does not support the standard createArrayOf method.
      Parameters:
      `arrayTypeName` - the name of the SQL type of the created object

      `elements` - the elements of the created object

      Returns:
      an ARRAY

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11.2.0.5.0

    <!-- -->

    - #### createBINARY_DOUBLE

          BINARY_DOUBLE createBINARY_DOUBLE(double value)
                                     throws SQLException

      Creates a BINARY_DOUBLE that has the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new BINARY_DOUBLE

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createBINARY_FLOAT

          BINARY_FLOAT createBINARY_FLOAT(float value)
                                   throws SQLException

      Creates a BINARY_FLOAT that has the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new BINARY_FLOAT

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createDATE

          DATE createDATE(Date value)
                   throws SQLException

      Creates a DATE that has the given value.
      Parameters:
      `value` - the value that the new object should repreesnt

      Returns:
      a new DATE

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createDATE

          DATE createDATE(Time value)
                   throws SQLException

      Creates a DATE that has the given value.
      Parameters:
      `value` - the value that the new object should repreesnt

      Returns:
      a new DATE

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createDATE

          DATE createDATE(Timestamp value)
                   throws SQLException

      Creates a DATE that has the given value.
      Parameters:
      `value` - the value that the new object should repreesnt

      Returns:
      a new DATE

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createDATE

          DATE createDATE(Date value,
                          Calendar cal)
                   throws SQLException

      Creates a DATE that has the given value. The value is interpreted as being in the time zone represented by cal.
      Parameters:
      `value` - the value that the new object should repreesnt

      `cal` - the timezone in which the value is interpreted

      Returns:
      a new DATE

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createDATE

          DATE createDATE(Time value,
                          Calendar cal)
                   throws SQLException

      Creates a DATE that has the given value. The value is interpreted as being in the time zone represented by cal.
      Parameters:
      `value` - the value that the new object should repreesnt

      `cal` - the timezone in which the value is interpreted

      Returns:
      a new DATE

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createDATE

          DATE createDATE(Timestamp value,
                          Calendar cal)
                   throws SQLException

      Creates a DATE that has the given value. The value is interpreted as being in the time zone represented by cal.
      Parameters:
      `value` - the value that the new object should repreesnt

      `cal` - the timezone in which the value is interpreted

      Returns:
      a new DATE

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createDATE

          DATE createDATE(String value)
                   throws SQLException

      Creates a DATE that has the given value.
      Parameters:
      `value` - the value that the new object should repreesnt

      Returns:
      a new DATE

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createINTERVALDS

          INTERVALDS createINTERVALDS(String value)
                               throws SQLException

      Creates an INTERVALDS that has the given value.
      Parameters:
      `value` - the value that the new object shoud represent

      Returns:
      a new INTERVALDS

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createINTERVALYM

          INTERVALYM createINTERVALYM(String value)
                               throws SQLException

      Creates an INTERVALYM that has the given value.
      Parameters:
      `value` - the value that the new object shoud represent

      Returns:
      a new INTERVALYM

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createNUMBER

          NUMBER createNUMBER(boolean value)
                       throws SQLException

      Creates a new NUMBER that has the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new NUMBER

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createNUMBER

          NUMBER createNUMBER(byte value)
                       throws SQLException

      Creates a new NUMBER that has the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new NUMBER

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createNUMBER

          NUMBER createNUMBER(short value)
                       throws SQLException

      Creates a new NUMBER that has the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new NUMBER

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createNUMBER

          NUMBER createNUMBER(int value)
                       throws SQLException

      Creates a new NUMBER that has the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new NUMBER

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createNUMBER

          NUMBER createNUMBER(long value)
                       throws SQLException

      Creates a new NUMBER that has the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new NUMBER

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createNUMBER

          NUMBER createNUMBER(float value)
                       throws SQLException

      Creates a new NUMBER that has the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new NUMBER

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createNUMBER

          NUMBER createNUMBER(double value)
                       throws SQLException

      Creates a new NUMBER that has the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new NUMBER

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createNUMBER

          NUMBER createNUMBER(BigDecimal value)
                       throws SQLException

      Creates a new NUMBER that has the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new NUMBER

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createNUMBER

          NUMBER createNUMBER(BigInteger value)
                       throws SQLException

      Creates a new NUMBER that has the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new NUMBER

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createNUMBER

          NUMBER createNUMBER(String value,
                              int scale)
                       throws SQLException

      Creates a new NUMBER that has the given value and scale.
      Parameters:
      `value` - the value that the new object should represent

      `scale` - the scale of the new object

      Returns:
      a new NUMBER

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMP

          TIMESTAMP createTIMESTAMP(Date value)
                             throws SQLException

      Creates a new TIMESTAMP with the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new TIMESTAMP

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMP

          TIMESTAMP createTIMESTAMP(DATE value)
                             throws SQLException

      Creates a new TIMESTAMP with the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new TIMESTAMP

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMP

          TIMESTAMP createTIMESTAMP(Time value)
                             throws SQLException

      Creates a new TIMESTAMP with the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new TIMESTAMP

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMP

          TIMESTAMP createTIMESTAMP(Timestamp value)
                             throws SQLException

      Creates a new TIMESTAMP with the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new TIMESTAMP

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMP

          TIMESTAMP createTIMESTAMP(Timestamp value,
                                    Calendar cal)
                             throws SQLException

      Creates a new TIMESTAMP with the given value.
      Parameters:
      `value` - the value that the new object should represent

      `cal` - the timezone of the value

      Returns:
      a new TIMESTAMP

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      12R2

    <!-- -->

    - #### createTIMESTAMP

          TIMESTAMP createTIMESTAMP(String value)
                             throws SQLException

      Creates a new TIMESTAMP with the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new TIMESTAMP

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMPTZ

          TIMESTAMPTZ createTIMESTAMPTZ(Date value)
                                 throws SQLException

      Creates a new TIMESTAMPTZ with the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new TIMESTAMPTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMPTZ

          TIMESTAMPTZ createTIMESTAMPTZ(Date value,
                                        Calendar cal)
                                 throws SQLException

      Creates a new TIMESTAMPTZ with the given value. The value is interpreted in the time zone of the calendar.
      Parameters:
      `value` - the value that the new object should represent

      `cal` - the timezone of the value

      Returns:
      a new TIMESTAMPTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMPTZ

          TIMESTAMPTZ createTIMESTAMPTZ(Time value)
                                 throws SQLException

      Creates a new TIMESTAMPTZ with the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new TIMESTAMPTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMPTZ

          TIMESTAMPTZ createTIMESTAMPTZ(Time value,
                                        Calendar cal)
                                 throws SQLException

      Creates a new TIMESTAMPTZ with the given value. The value is interpreted in the time zone of the calendar.
      Parameters:
      `value` - the value that the new object should represent

      `cal` - the timezone of the value

      Returns:
      a new TIMESTAMPTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMPTZ

          TIMESTAMPTZ createTIMESTAMPTZ(Timestamp value)
                                 throws SQLException

      Creates a new TIMESTAMPTZ with the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new TIMESTAMPTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMPTZ

          TIMESTAMPTZ createTIMESTAMPTZ(Timestamp value,
                                        Calendar cal)
                                 throws SQLException

      Creates a new TIMESTAMPTZ with the given value. The value is interpreted in the time zone of the calendar.
      Parameters:
      `value` - the value that the new object should represent

      `cal` - the timezone of the value

      Returns:
      a new TIMESTAMPTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMPTZ

          TIMESTAMPTZ createTIMESTAMPTZ(Timestamp value,
                                        java.time.ZoneId tzid)
                                 throws SQLException

      Creates a new TIMESTAMPTZ with the given value.
      Parameters:
      `value` - the value that the new object should represent

      `tzid` - the ZoneId of the value

      Returns:
      a new TIMESTAMPTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMPTZ

          TIMESTAMPTZ createTIMESTAMPTZ(String value)
                                 throws SQLException

      Creates a new TIMESTAMPTZ with the given value.
      Parameters:
      `value` - the value that the new object should represent

      Returns:
      a new TIMESTAMPTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMPTZ

          TIMESTAMPTZ createTIMESTAMPTZ(String value,
                                        Calendar cal)
                                 throws SQLException

      Creates a new TIMESTAMPTZ with the given value. The value is interpreted in the time zone of the calendar.
      Parameters:
      `value` - the value that the new object should represent

      `cal` - the timezone of the value

      Returns:
      a new TIMESTAMPTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMPTZ

          TIMESTAMPTZ createTIMESTAMPTZ(DATE value)
                                 throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMPLTZ

          TIMESTAMPLTZ createTIMESTAMPLTZ(Date value,
                                          Calendar cal)
                                   throws SQLException

      Creates a new TIMESTAMPLTZ with the given value. The value is interpreted in the time zone of the calendar.
      Parameters:
      `value` - the value that the new object should represent

      `cal` - the timezone of the value

      Returns:
      a new TIMESTAMPLTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMPLTZ

          TIMESTAMPLTZ createTIMESTAMPLTZ(Time value,
                                          Calendar cal)
                                   throws SQLException

      Creates a new TIMESTAMPLTZ with the given value. The value is interpreted in the time zone of the calendar.
      Parameters:
      `value` - the value that the new object should represent

      `cal` - the timezone of the value

      Returns:
      a new TIMESTAMPLTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMPLTZ

          TIMESTAMPLTZ createTIMESTAMPLTZ(Timestamp value,
                                          Calendar cal)
                                   throws SQLException

      Creates a new TIMESTAMPLTZ with the given value. The value is interpreted in the time zone of the calendar.
      Parameters:
      `value` - the value that the new object should represent

      `cal` - the timezone of the value

      Returns:
      a new TIMESTAMPLTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMPLTZ

          TIMESTAMPLTZ createTIMESTAMPLTZ(String value,
                                          Calendar cal)
                                   throws SQLException

      Creates a new TIMESTAMPLTZ with the given value. The value is interpreted in the time zone of the calendar.
      Parameters:
      `value` - the value that the new object should represent

      `cal` - the timezone of the value

      Returns:
      a new TIMESTAMPLTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### createTIMESTAMPLTZ

          TIMESTAMPLTZ createTIMESTAMPLTZ(DATE value,
                                          Calendar cal)
                                   throws SQLException

      Creates a new TIMESTAMPLTZ with the given value. The value is interpreted in the time zone of the calendar.
      Parameters:
      `value` - the value that the new object should represent

      `cal` - the timezone of the value

      Returns:
      a new TIMESTAMPLTZ

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database error occurs

      Since:
      11R1

    <!-- -->

    - #### cancel

          void cancel()
               throws SQLException

      Performs an immediate (asynchronous) termination of any currently executing operation on this connection. It is normally used to stop a long-running JDBC call being processed on the server. It can be called by a user thread in multithreaded applications.
      For example, in the context of AQ, it can be used to cancel a 'dequeue' call that is waiting for a new message to be enqueued.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the cancel operation fails

    <!-- -->

    - #### abort

          void abort()
              throws SQLException

      Calling abort() on an open connection does the following: marks the connection as closed, closes any sockets or other primitive connections to the database, and insures that any thread that is currently accessing the connection will either progress to completion of the JDBC call or throw an exception. Calling abort() on a closed connection does nothing. It is critical to note that abort() does not hang. It does not block because of pending database operations. In particular it is not synchronized. Since typically abort() will be called when it appears that the connection is dead, any attempt to communicate with the database via blocking IO is likely to hang and is not attempted. As such, abort leaves the connection in a unknown state. Although abort marks the connection as closed, it does not release any local resources as it cannot do so safely; it is not synchronized. It is recommended to call Connection.close() after calling abort. Connection.close() will recognize that connection has been aborted and will clean up local resources, even though the connection has already been marked as closed. Since Connection.close is synchronized it may hang briefly while any thread that has a lock on the connection completes and releases the lock. Recall that after calling abort any thread that is using the connection will be able to proceed to completion or will throw an exception. abort is very different from OracleConnection.cancel. cancel gracefully stops the execution of any SQL operation. It is a synchronous operation that communicates with the database. It leaves the connection and the statements in a well-known and usable state. In contrast abort tears down the client side network connection to the database, leaving the server to clean up as best it can whenever it discovers that the connection has been broken. abort does not clean up client side resources and leaves the connection and associated statements in an unknown and unusable state. The only valid thing to do with a connection after calling abort is to call close and then discard the connection object. After calling cancel the app can continue to use the connection and statements. If there is a security manager, its checkPermission method is called with an oracle.jdbc.OracleSQLPermission("callAbort") permission to see if the caller has permission to abort a connection. If the caller does not have permission, a SecurityException is thrown. See the ojdbc.policy file in the demo directory for help in granting the appropriate permissions when using a SecurityManager with Oracle JDBC. The best use of the abort() call is in the layer that manages connections such as the connection pool. Stale or invalid connections may often appear to hang when an application thread is blocked on a network call. Connection pools may implement a cleaner thread, that simply looks for such stale connections and issues the abort() call. This results in releasing all client handles and resources without expecting an acknowledgement from the database backend. There is no need for user code to call abort when using an Oracle connection pool such as the Implicit Connection Cache or the Universal Connection Pool as these connection pools will call abort when necessary.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - -- Io Exception: Socket closed - ORA-17002 TNS:not connected - ORA-12153

      [`SecurityException`](http://download.oracle.com/javase/8/docs/api/java/lang/SecurityException.html?is-external=true) - if the caller does not have the necessary permission

      Since:
      11.0

    <!-- -->

    - #### getAllTypeDescriptorsInCurrentSchema

          TypeDescriptor[] getAllTypeDescriptorsInCurrentSchema()
                                                         throws SQLException

      Obtain all the type descriptors associated with object types or array in the schema of this connection. Note that synonyms are not suportted. Requires an internal PL/SQL package that is present only in database 11 and above.
      Returns:
      An array of the appropriate descriptors for Arrays or Structs depending on the type names found.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If an error occurs.

      Since:
      11.1

    <!-- -->

    - #### getTypeDescriptorsFromListInCurrentSchema

          TypeDescriptor[] getTypeDescriptorsFromListInCurrentSchema(String[] typeNames)
                                                              throws SQLException

      Obtain the type descriptors associated with object types or array in a schema from an array of type names. Note that synonyms are not suportted. Requires an internal PL/SQL package that is present only in database 11 and above.
      Parameters:
      `An` - array of Strings which are type names. Use upper case unless the type names are mixed case names.

      Returns:
      An array of the appropriate descriptors for Arrays or Structs depending on the type names found.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the specified type does not exist, or if an error occurred.

      Since:
      11.1

    <!-- -->

    - #### getTypeDescriptorsFromList

          TypeDescriptor[] getTypeDescriptorsFromList(String[][] schemaAndTypeNamePairs)
                                               throws SQLException

      Obtain the type descriptors associated with object types or arrays from an array of scheama and type names. Note that synonyms are not suportted. Requires an internal PL/SQL package that is present only in database 11 and above.
      Parameters:
      `An` - array of arrays of Strings which are pairs of schema and type names.

      Returns:
      An array of the appropriate descriptors for Arrays or Structs depending on the type names found.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if any of the specified types does not exist, or if an error occurs.

      Since:
      11.1

    <!-- -->

    - #### getDataIntegrityAlgorithmName

          String getDataIntegrityAlgorithmName()
                                        throws SQLException

      Returns the name of the algorithm that is used for data integrity checking by the thin driver on the network. Returns "" when there is no data integrity checking.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getEncryptionAlgorithmName

          String getEncryptionAlgorithmName()
                                     throws SQLException

      Returns the name of the algorithm that is used for data encryption by the thin driver on the network. Returns "" when the data isn't encrypted on the network.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getAuthenticationAdaptorName

          String getAuthenticationAdaptorName()
                                       throws SQLException

      Returns the name of the adaptor that is used for authentication by the thin driver. Returns "" for basic user/password authenticatin.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isUsable

          boolean isUsable()

      Identifies whether this connection is still usable for JDBC operations.
      Returns:
      true if this connection is usable; false otherwise.

    <!-- -->

    - #### setDefaultTimeZone

          void setDefaultTimeZone(TimeZone tz)
                           throws SQLException

      The TimeZone to be used while creating java.sql.Date, java.sql.Time & java.sql.Timestamp.
      Parameters:
      `Default` - TimeZone to be used for all Date, Time and Timestamp conversions.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an issue while setting the TimeZone

    <!-- -->

    - #### getDefaultTimeZone

          TimeZone getDefaultTimeZone()
                               throws SQLException

      Returns the TimeZone set through setDefaultTimeZone.
      Returns:
      TimeZone set through setDefaultTimeZone. Returns null if TimeZone if setDefaultTimeZone in not invoked with proper values.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If there is any issue while retrieving the TimeZone

    <!-- -->

    - #### setApplicationContext

          void setApplicationContext(String nameSpace,
                                     String attribute,
                                     String value)
                              throws SQLException

      Deprecated. This has been deprecated since 12.1 in favour of setClientInfo(). It is not recommended to use this API intermingled with get/setClientInfo APIs.
      Sets a attribute/value pair in a particular namespace in the application context on the server. This application context is stored in the user session. Note that you can call this method multiple times to set more than one attribute/value pair in the application context. Please note that the only supported namespace is CLIENTCONTEXT. More may be added in a future release. This method does not require any additional roundtrip.
      Parameters:
      `nameSpace` - The namespace where this attribute/value pairs will be stored. The only supported namespace is CLIENTCONTEXT. The value cannot be null nor empty.

      `attribute` - The attribute whose value needs to be set. If the value is null then a NullPointerException is thrown. If the value is an empty string (""), then the namespace will be cleared and the value is ignored.

      `value` - The value of the attribute. If the value is null then a NullPointerException is thrown. If the value is an empty string (""), then the attribute will be cleared.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If an error occurs

      See Also:
      `clearAllApplicationContext`, [`Connection.setClientInfo(java.lang.String, java.lang.String)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setClientInfo_java_lang_String_java_lang_String_), [`Connection.setClientInfo(java.util.Properties)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setClientInfo_java_util_Properties_)

    <!-- -->

    - #### clearAllApplicationContext

          void clearAllApplicationContext(String nameSpace)
                                   throws SQLException

      Deprecated. This is deprecated since 12.1 in favor of the standard JDBC API setClientInfo(). It is not recommended to use this API intermingled with get/setClientInfo APIs.
      Clear all the attribute/value information in a namespace.
      Parameters:
      `nameSpace` - The namespace which will be cleared

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `setApplicationContext`, [`Connection.setClientInfo(java.util.Properties)`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#setClientInfo_java_util_Properties_)

    <!-- -->

    - #### addLogicalTransactionIdEventListener

          void addLogicalTransactionIdEventListener(LogicalTransactionIdEventListener listener)
                                             throws SQLException

      Registers a listener to Logical Transaction Id events. The caller is responsible for writing an implementation of the `LogicalTransactionIdEventListener` interface. A listener instance must then be registered using this method.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### addLogicalTransactionIdEventListener

          void addLogicalTransactionIdEventListener(LogicalTransactionIdEventListener listener,
                                                    Executor executor)
                                             throws SQLException

      This flavor of `addLogicalTransactionIdEventListener` can be used to register a listener with an executor. When a Logical Transaction Id event is triggered the driver will use this executor to call the listener's `onLogicalTransactionIdEvent` method. Typically you would call this method if you want `onLogicalTransactionIdEvent` to be executed in a separate thread.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### removeLogicalTransactionIdEventListener

          void removeLogicalTransactionIdEventListener(LogicalTransactionIdEventListener listener)
                                                throws SQLException

      Deregisters the Logical Transaction Id event listener.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getLogicalTransactionId

          LogicalTransactionId getLogicalTransactionId()
                                                throws SQLException

      Gets the current Logical Transaction Id which are sent by the server in a piggy back message and hence this method call doesn't make a roundtrip.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isDRCPEnabled

          boolean isDRCPEnabled()
                         throws SQLException

      Returns `true` if the connection is participating in DRCP.
      Returns:
      true if DRCP is enabled

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error while processing the request

      See Also:
      `attachServerConnection()`, `detachServerConnection(java.lang.String)`, `needToPurgeStatementCache()`

    <!-- -->

    - #### isDRCPMultitagEnabled

          boolean isDRCPMultitagEnabled()
                                 throws SQLException

      Returns true if multiple tags are allowed with DRCP Connection.
      Returns:
      true if DRCP multitagging is enabled.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `CONNECTION_PROPERTY_USE_DRCP_MULTIPLE_TAG`

    <!-- -->

    - #### getDRCPReturnTag

          String getDRCPReturnTag()
                           throws SQLException

      Returns the tag associated with this DRCP pooled server. If multiple tags are used, they will be separated by a semicolon. If tagging is not enabled or not available or if this connection is currently not attached to any DRCP pooled server then this method returns null.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `detachServerConnection(java.lang.String)`, `CONNECTION_PROPERTY_USE_DRCP_MULTIPLE_TAG`

    <!-- -->

    - #### getDRCPPLSQLCallbackName

          String getDRCPPLSQLCallbackName()
                                   throws SQLException

      Returns the PL/SQL Fix-up callback name if configured, otherwise returns `Null`
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `CONNECTION_PROPERTY_DRCP_PLSQL_CALLBACK`, `CONNECTION_PROPERTY_USE_DRCP_MULTIPLE_TAG`

    <!-- -->

    - #### attachServerConnection

          boolean attachServerConnection()
                                  throws SQLException

      This method needs to be called before using a DRCP connection. This method is a local call when used without tagging and will return immediately. The server process from the specified connection class is obtained during the next roundtrip to the server. So the database roundtrip after attachServerConnection will take longer than usual. However when tagging is used this call makes a roundtrip to obtain a server process from the same connection class. So invoking this call will wait until a server process is available for this session.
      Multiple invocation of this method with tagging will not make multiple roundtrips to the database instead return the status from the previous call.

      Invoking this method on a non DRCP connection or invoking this method multiple times in a non-tagging case is a noop and will return `true`. Invoking this method multiple times in a tagging case will return the tag match status.

      `needToPurgeStatementCache()` returns `true` if the underlying session has changed and if the local statement cache should be purged.

      Returns:
      true - If the tag matched. In cases without tagging it returns `true` by default

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If there is an exception while obtaining server process

      Since:
      12.1

      See Also:
      `isDRCPEnabled()`, `detachServerConnection(java.lang.String)`, `needToPurgeStatementCache()`

    <!-- -->

    - #### detachServerConnection

          void detachServerConnection(String tag)
                               throws SQLException

      Notify the server that this connection will not be used. The server can choose to reuse the server process if needed. The connection can be released with a tag which ensures upon that the next `attachServerConnection()` on this connection the server will attempt to pair this connection with the server process of the same tag.
      This method makes a one way call to the database for performance reasons. However the call is two way when the connection is participating in a Transaction

      Parameters:
      `tag` - A string value that the connection will be associated in the the server. `null` is a valid argument when no tagging required. An empty String will be treated the same as null.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - If there was an exception while releasing

      Since:
      12.1

      See Also:
      `isDRCPEnabled()`, `attachServerConnection()`, `needToPurgeStatementCache()`

    <!-- -->

    - #### needToPurgeStatementCache

          boolean needToPurgeStatementCache()
                                     throws SQLException

      Returns if the client side Statement cache has to be purged. This method informs the connection managers if the local statement cache should be purged.
      Returns:
      `true` to purge the statement cache

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an exception while performing this operation.

      Since:
      12.1

      See Also:
      `isDRCPEnabled()`, `attachServerConnection()`, `detachServerConnection(java.lang.String)`

    <!-- -->

    - #### getDRCPState

          OracleConnection.DRCPState getDRCPState()
                                           throws SQLException

      Returns an enum indicating if the connection is attached to a DRCP server process.
      Returns:
      [`OracleConnection.DRCPState.DETACHED`](OracleConnection.DRCPState.md) if the connection is detached. [`OracleConnection.DRCPState.ATTACHED_IMPLICIT`](OracleConnection.DRCPState.md) or [`OracleConnection.DRCPState.ATTACHED_EXPLICIT`](OracleConnection.DRCPState.md) if the connection is attached.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      12.2

      See Also:
      `attachServerConnection()`, `detachServerConnection(java.lang.String)`, `isDRCPEnabled()`

    <!-- -->

    - #### beginRequest

          void beginRequest()
                     throws SQLException

      Declares that a request to the server is starting on this connection. When called after another beginRequest() but before an endRequest(), this call is a no-op and does not throw any exception. Therefore, application is allowed to call beginRequest after a connection pool checkout, which implicitly calls beginRequest.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - When called with an open transaction on this connection.

    <!-- -->

    - #### endRequest

          void endRequest()
                   throws SQLException

      Declares that the request that was in progress on this connection has completed. Existing connection labels and state on the connection are not affected by this call. Calling endRequest() multiple times without beginRequest() in-between is allowed.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - When called with an open transaction on this connection.

    <!-- -->

    - #### setShardingKeyIfValid

          boolean setShardingKeyIfValid(OracleShardingKey shardingKey,
                                        OracleShardingKey superShardingKey,
                                        int timeout)
                                 throws SQLException

      Checks the validity of the connection and also checks if the sharding keys passed to this method are valid for the connection.If the sharding keys are valid, it will be set on the connection.
      Parameters:
      `shardingKey` - Sharding key to be validated and set against this connection

      `superShardingKey` - Super Sharding key to be validated and set against this connection

      `timeout` - Time in seconds before which the validation process is expected to be complete, else the validation process is aborted. The value of the timeout must be set to zero to disable the timeout during the validation.

      Returns:
      true if the connection is valid and the shard keys are valid to be set on this connection.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is any exception while performing this validation or if timeout value is less than 0.

    <!-- -->

    - #### setShardingKey

          void setShardingKey(OracleShardingKey shardingKey,
                              OracleShardingKey superShardingKey)
                       throws SQLException

      Sets the sharding key and the super sharding key on this connection.
      Parameters:
      `shardingKey` - Sharding key to be set on this connection

      `superShardingKey` - Super Sharding key to be set on this connection

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an exception while setting the sharding keys on this connection.

    <!-- -->

    - #### setShardingKeyIfValid

          boolean setShardingKeyIfValid(OracleShardingKey shardingKey,
                                        int timeout)
                                 throws SQLException

      Checks the validity of the connection and also checks if the sharding key passed to this method is valid for the connection.If the sharding key is valid, it will be set on the connection.
      Parameters:
      `shardingKey` - Sharding key to be validated and set against this connection

      `timeout` - Time in seconds before which the validation process is expected to be complete, else the validation process is aborted. The value of the timeout must be set to zero to disable the timeout during the validation.

      Returns:
      true if the connection is valid and the shard keys are valid to be set on this connection.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is any exception while performing this validation or if timeout value is less than 0.

    <!-- -->

    - #### setShardingKey

          void setShardingKey(OracleShardingKey shardingKey)
                       throws SQLException

      Sets the sharding key on this connection.
      Parameters:
      `shardingKey` - Sharding key to be set on this connection

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an exception while setting the sharding keys on this connection.

    <!-- -->

    - #### isValid

          boolean isValid(OracleConnection.ConnectionValidation effort,
                          int timeout)
                   throws SQLException

      Returns true if this connection was working properly to the extent specified by `effort` at the instant during this call it was checked. It does not imply it is still working after the call returns, only it worked at some point during the call. Returns false if the connection is not working properly at the instant during the call when it is checked or if the timeout is exceeded while checking.
      Parameters:
      `timeout` - The time in seconds to wait for the validation action to complete. If the timeout expires before the action completes the method returns false. A value of 0 mean no limit.

      `effort` - How much effort to expend checking the connection.

      Returns:
      true if the connection is valid, false otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if timeout \< 0

    <!-- -->

    - #### getEncryptionProviderName

          String getEncryptionProviderName()
                                    throws SQLException

      If network encryption service is enabled, returns the name of the encryption provider, otherwise returns `null`.
      Returns:
      encryptionProviderName

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `CONNECTION_PROPERTY_THIN_NET_ENCRYPTION_LEVEL`

    <!-- -->

    - #### getChecksumProviderName

          String getChecksumProviderName()
                                  throws SQLException

      If network integrity service is enabled, returns the name of the checksum provider, otherwise returns `null`.
      Returns:
      checksumProviderName

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `CONNECTION_PROPERTY_THIN_NET_CHECKSUM_LEVEL`

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleClob.md)
- [Next Class](OracleConnection.CommitOption.md)

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
