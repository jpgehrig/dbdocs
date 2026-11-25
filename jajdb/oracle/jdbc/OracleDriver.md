Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleDriver.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleDataFactory.md)
- [Next Class](OracleNClob.md)

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

## Class OracleDriver

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.driver.OracleDriver

  - - oracle.jdbc.OracleDriver

<!-- -->

- All Implemented Interfaces:
  [Driver](http://download.oracle.com/javase/8/docs/api/java/sql/Driver.html?is-external=true)

  ------------------------------------------------------------------------



      public class OracleDriver
      extends oracle.jdbc.driver.OracleDriver

  The Oracle JDBC driver class that implements the `java.sql.Driver` interface.
  # Register the JDBC drivers

  To access a database from a Java application, you must first provide the code to register your installed driver with your program. You do this with the static `registerDriver()` method of the `java.sql.DriverManager` class. This class provides a basic service for managing a set of JDBC drivers. The `registerDriver()` method takes as input a "driver" class, that is, a class that implements the `java.sql.Driver` interface, as is the case with `OracleDriver`.

  **Note:** Alternatively, you can use the `forName()` method of the `java.lang.Class` class to load the JDBC drivers directly. For example: `Class.forName ("oracle.jdbc.OracleDriver");`. However, this method is valid only for JDK-compliant Java virtual machines. It is not valid for Microsoft Java virtual machines.

  You register the driver only once in your Java application.

        DriverManager.registerDriver (new oracle.jdbc.OracleDriver());


  # Open a Connection to a database

  Once you have registered the driver, you can open a connection to the database with the static `getConnection()` method of the `java.sql.DriverManager` class. The type of the object returned is `java.sql.Connection`.

  ## Understanding the Forms of getConnection()

  ### Specifying a Databse URL, User Name, and Password

  The following signature takes the URL, user name, and password as separate parameters:

  `getConnection(String URL, String user, String password);`

  Where the URL is of the form:
    `jdbc:oracle:<drivertype>:@<database>`

  The following example connects user `scott` with password `tiger` to a database with SID `orcl` through port 1521 of host `myhost`, using the Thin driver.

  `Connection conn = DriverManager.getConnection`
  `  ("jdbc:oracle:thin:@myhost:1521:orcl", "scott", "tiger");`

  ### Specifying a Databse URL That Includes User Name and Password

  The following signature takes the URL, user name, and password all as part of a URL parameter:

  `getConnection(String URL);`

  Where the URL is of the form:
    `jdbc:oracle:<drivertype>:<user>/<password>@<database>`

  The following example connects user `scott` with password `tiger` to a database on host `myhost` using the OCI driver. In this case, however, the URL includes the userid and password, and is the only input parameter.

  `Connection conn = DriverManager.getConnection`
  `   ("jdbc:oracle:oci8:scott/tiger@myhost);`

  If you want to connect with the Thin driver, you must specify the port number and SID. For example, if you want to connect to the database on host `myhost` that has a TCP/IP listener up on port 1521, and the `SID` (system identifier) is `orcl`:

  `Connection conn = DriverManager.getConnection`
  `   ("jdbc:oracle:thin:scott/tiger@myhost:1521:orcl);`

  ### Specifying a Database URL and Properties Object

  The following signature takes a URL, together with a properties object that specifies user name and password (perhaps among other things):

  `getConnection(String URL, Properties info);`

  Where the `URL` is of the form:
    `jdbc:oracle:<drivertype>:@<database>`

  In addition to the URL, use an object of the standard Java `Properties` class as input. For example:

  `java.util.Properties info = new java.util.Properties();`
  `  info.put ("user", "scott");`
  `  info.put (`"password",`"tiger"`);
    info.put ("defaultRowPrefetch","15");
    getConnection ("jdbc:oracle:oci8:@",info);

  The table below lists the connection properties that Oracle JDBC drivers support.

  **Connection Properties Recognized by Oracle JDBC Drivers**

  | **Name**                    | **Short Name** | **Type**                           | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
  |-----------------------------|----------------|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | user                        | n/a            | String                             | the user name for logging into the database                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
  | password                    | n/a            | String                             | the password for logging into the database                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
  | database                    | server         | String                             | the connect string for the database                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
  | internal_logon              | n/a            | String                             | a role, such as `sysdba` or `sysoper`, that allows you to log on as `sys`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
  | defaultRowPrefetch          | prefetch       | String (containing integer value)  | the default number of rows to prefetch from the server (default value is "10")                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
  | remarksReporting            | remarks        | String (containing boolean value)  | "true" if getTables() and getColumns() should report TABLE_REMARKS; equivalent to using setRemarksReporting() (default value is "false")                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
  | defaultBatchValue           | batchvalue     | String (containing integer value)  | the default batch value that triggers an execution request (default value is "10")                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
  | includeSynonyms             | synonyms       | String (containing boolean value)  | "true" to include column information from predefined "synonym" SQL entities when you execute a `DataBaseMetaData getColumns()` call; equivalent to connection `setIncludeSynonyms()` call (default value is "false")                                                                                                                                                                                                                                                                                                                                                                                                                             |
  | processEscapes              | n/a            | String (containing boolean value)  | "false" to disable escape processing for statements (Statement or PreparedStatement) created from this connection. Set this to "false" if you want to avoid many calls to `Statement.setEscapeProcessing(false);`. This is espcially usefull for PreparedStatement where a call to `setEscapeProcessing(false)` would have no effect. The default is "true".                                                                                                                                                                                                                                                                                     |
  | defaultNChar                | n/a            | String (containing boolean value)  | "false" is the default. If set to "true", the default behavior for handling character datatypes is changed so that NCHAR/NVARCHAR2 become the default. This means that setFormOfUse() won't be needed anymore when using NCHAR/NVARCHAR2. This can also be set as a java property :<br>`java -Doracle.jdbc.defaultNChar=true myApplication`                                                                                                                                                                                                                                                                                                      |
  | useFetchSizeWithLongColumn  | n/a            | String (containing boolean value)  | "false" is the default.<br>**THIS IS A THIN ONLY PROPERTY. IT SHOULD NOT BE USED WITH ANY OTHER DRIVERS.**<br>If set to "true", the performance when retrieving data in a 'SELECT' will be improved but the default behavior for handling LONG columns will be changed to fetch multiple rows (prefetch size). It means that enough memory will be allocated to read this data. So if you want to use this property, make sure that the LONG columns you are retrieving are not too big or you may run out of memory. This property can also be set as a java property :<br>`java -Doracle.jdbc.useFetchSizeWithLongColumn=true myApplication`   |
  | SetFloatAndDoubleUseBinary  | n/a            | String (containing boolean value)  | "false" is the default.<br>If set to "true", causes the java.sql.PreparedStatment setFloat and setDouble API's to use internal binary format as for BINARY_FLOAT and BINARY_DOUBLE parameters.<br>See oracle.jdbc.OraclePreparedStatement setBinaryFloat and setBinaryDouble<br>                                                                                                                                                                                                                                                                                                                                                                 |

  ## Select your driver type : thin, oci, kprb...

  Oracle provides four types of JDBC driver.

  - **Thin Driver**, a 100% Java driver for client-side use without an Oracle installation, particularly with applets. The Thin driver type is `thin`. To connect user `scott` with password `tiger` to a database with `SID` (system identifier) `orcl` through port 1521 of host `myhost`, using the Thin driver, you would write :

          Connection conn = DriverManager.getConnection
          ("jdbc:oracle:thin:@myhost:1521:orcl", "scott", "tiger");


  - **OCI Driver** for client-side use with an Oracle client installation. The OCI driver type is `oci`. To connect user `scott` with password `tiger` to a database with `SID` (system identifier) `orcl` through port 1521 of host `myhost`, using the OCI driver, you would write :

          Connection conn = DriverManager.getConnection
          ("jdbc:oracle:oci:@myhost:1521:orcl", "scott", "tiger");


    Note that you can also specify the database by a `TNSNAMES` entry. You can find the available `TNSNAMES` entries listed in the file `tnsnames.ora` on the client computer from which you are connecting. For example, if you want to connect to the database on host `myhost` as user `scott` with password `tiger` that has a `TNSNAMES` entry of `MyHostString`, enter:

          Connection conn = DriverManager.getConnection
          ("jdbc:oracle:oci8:@MyHostString","scott","tiger");


    If your JDBC client and Oracle server are running on the same machine, the OCI driver can use IPC (InterProcess Communication) to connect to the database instead of a network connection. An IPC connection is much faster than a network connection.

          Connection conn = DriverManager.getConnection
          ("jdbc:oracle:oci8:@","scott","tiger");


  - **Server-Side Thin Driver**, which is functionally the same as the client-side Thin driver, but is for code that runs inside an Oracle server and needs to access a remote server, including middle-tier scenarios. The Server-Side Thin driver type is `thin` and there is no difference in your code between using the Thin driver from a client application or from inside a server.

  - **Server-Side Internal Driver** for code that runs inside the target server, that is, inside the Oracle server that it must access. The Server-Side Internal driver type is `kprb` and it actually runs within a default session. You are already "connected". Therefore **the connection should never be closed**.
    To access the default connection, write:

          DriverManager.getConnection("jdbc:oracle:kprb:");
          or:
          DriverManager.getConnection("jdbc:default:connection:");


    You can also use the Oracle-specific defaultConnection() method of the OracleDriver class which is generally recommended:

          OracleDriver ora = new OracleDriver();
          Connection conn = ora.defaultConnection();


    **Note:** You are no longer required to register the `OracleDriver` class for connecting with the Server-Side Internal driver, although there is no harm in doing so. This is true whether you are using `getConnection()` or `defaultConnection()` to make the connection.
    Any user name or password you include in the URL string is ignored in connecting to the server default connection. The `DriverManager.getConnection()` method returns a new Java `Connection` object every time you call it. Note that although the method is not creating a new physical connection (only a single implicit connection is used), it is returning a new object.
    Again, when JDBC code is running inside the target server, the connection is an implicit data channel, not an explicit connection instance as from a client. It should never be closed.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.jdbc.driver.OracleDriver

      `access_string, accumulate_batch_result, batch_string, convert_nchar_literals_string, database_string, dataSizeBytes, dataSizeChars, dataSizeUnitsPropertyName, DEFAULT_CONNECTION_PROPERTIES, default_execute_batch_string, default_row_prefetch_string, defaultConn, defaultnchar_string, defaultncharprop_string, disable_defineColumnType_string, dll_string, execute_batch_string, fixed_string_string, include_synonyms_string, j2ee_compliance, jdbc_string, logon_as_internal_str, nls_lang_backdoor, no_caching_buffers, oracle_string, password_string, permit_timestamp_date_mismatch_string, prefetch_string, prelim_auth_string, process_escapes_string, protocol_string, protocolFullName_string, proxy_client_name, read_timeout, remarks_string, report_remarks_string, restrict_getTables_string, retain_v9_bind_behavior_string, row_prefetch_string, server_string, set_new_password_string, SetFloatAndDoubleUseBinary_string, synonyms_string, systemTypeMap, tcp_no_delay, useFetchSizeWithLongColumn_prop_string, useFetchSizeWithLongColumn_string, user_string, v8compatible_string, xa_trans_loose`

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `OracleDriver``()`          |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                        | Method and Description                                                                                                                                                                        |
    |----------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getBuildDate``()`<br>Returns a String that specifies exactly when the jar file was built.                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getDriverVersion``()`<br>Returns a String that specifies the Oracle version number of the driver.                                                                                            |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getJDBCVersion``()`<br>Returns a String that specifies the version of the JDBC spec supporte by the driver.                                                                                  |
    | `static boolean`                                                                                         | `isDebug``()`<br>Returns true if this jar includes debug code.                                                                                                                                |
    | `static boolean`                                                                                         | `isDMS``()`<br>Returns true if this jar includes DMS instrumentaion.                                                                                                                          |
    | `static boolean`                                                                                         | `isInServer``()`<br>Returns true if this jar was built to run in the Oracle Java VM.                                                                                                          |
    | `static boolean`                                                                                         | `isJDK14``()`<br>Deprecated.                                                                                                                                                                  |
    | `static boolean`                                                                                         | `isPrivateDebug``()`<br>Returns true if this jar includes Oracle internal debug code.                                                                                                         |
    | `static void`                                                                                            | `main``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] args)`<br>Prints a description of the Oracle JDBC driver .jar file to System.out. |

    - ### Methods inherited from class oracle.jdbc.driver.OracleDriver

      `acceptsURL, connect, connect, connect, defaultConnection, getCompileTime, getExecutorService, getMajorVersion, getMinorVersion, getParentLogger, getPropertyInfo, getSystemPropertyDateZeroTime, getSystemPropertyDateZeroTimeExtra, getSystemPropertyFastConnectionFailover, jdbcCompliant, processSqlEscapes, registerMBeans, setExecutorService, unRegisterMBeans`

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### OracleDriver

          public OracleDriver()

  <!-- -->

  - ### Method Detail

    - #### isDMS

          public static final boolean isDMS()

      Returns true if this jar includes DMS instrumentaion.
      Returns:
      true if DMS jar

    <!-- -->

    - #### isInServer

          public static final boolean isInServer()

      Returns true if this jar was built to run in the Oracle Java VM.
      Returns:
      true if server jar

    <!-- -->

    - #### isJDK14

          public static final boolean isJDK14()

      Deprecated. 
      Returns true if this is a JDK 1.4 or later compliant jar. Since JDK 1.3 is desupported, always returns true.
      Returns:
      true

    <!-- -->

    - #### isDebug

          public static final boolean isDebug()

      Returns true if this jar includes debug code.
      Returns:
      true if debug jar

    <!-- -->

    - #### isPrivateDebug

          public static final boolean isPrivateDebug()

      Returns true if this jar includes Oracle internal debug code.
      Returns:
      true if private debug jar

    <!-- -->

    - #### getJDBCVersion

          public static final String getJDBCVersion()

      Returns a String that specifies the version of the JDBC spec supporte by the driver.
      Returns:
      JDBC spec version

    <!-- -->

    - #### getDriverVersion

          public static final String getDriverVersion()

      Returns a String that specifies the Oracle version number of the driver.
      Returns:
      version number

    <!-- -->

    - #### getBuildDate

          public static final String getBuildDate()

      Returns a String that specifies exactly when the jar file was built.
      Returns:
      build date

    <!-- -->

    - #### main

          public static void main(String[] args)
                           throws Exception

      Prints a description of the Oracle JDBC driver .jar file to System.out.
      Parameters:
      `args` - Ignored

      Throws:
      [`Exception`](http://download.oracle.com/javase/8/docs/api/java/lang/Exception.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleDriver.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleDataFactory.md)
- [Next Class](OracleNClob.md)

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
