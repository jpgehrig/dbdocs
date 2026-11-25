Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](TIN2Contours.md)
- [Next Class](Util.CheckType.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.util

## Class Util

- java.lang.Object

- - oracle.spatial.util.Util

<!-- -->

-

  ------------------------------------------------------------------------



      public class Util
      extends java.lang.Object

  some useful utility routines used by SDOVIS. These are not clearly documented so use at your own risk!! This is internal.

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                  |
    |-------------------|----------------------------------------|
    | `static class `   | [`Util.CheckType`](Util.CheckType.md)  |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `Util``()`                  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                                                                                                                               |
    |-------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`                             | `center``(java.awt.Component c)`<br>Centers an awt component w.r.t.                                                                                                                                                                                                                  |
    | `static java.lang.String`                 | `checkSQLName``(java.lang.String string, int maxStringLength)`<br>Checks for any illegal characters in a SQL name.                                                                                                                                                                   |
    | `static java.lang.String`                 | `checkSQLName``(java.lang.String string, int maxStringLength, `[`Util.CheckType`](Util.CheckType.md)` checkType)`<br>Checks: - for any illegal characters in a SQL name.                                                                                                             |
    | `static java.sql.Connection`              | `connect``(java.lang.String host, java.lang.String sid, java.lang.String port, java.lang.String user, java.lang.String passwd, java.lang.String mode, int rowPref)`<br>Establishes an Oracle JDBC connection to the specified database.                                              |
    | `static double[]`                         | `convert``(java.lang.String str)`<br>Converts a string of coordinates into a double array.                                                                                                                                                                                           |
    | `static java.lang.String`                 | `enquoteColumnName``(java.sql.Connection conn, java.lang.String columnName)`<br>Enquotes a column name.                                                                                                                                                                              |
    | `static java.lang.String`                 | `enquoteNameSQLName``(java.sql.Connection conn, java.lang.String name)`<br>Returns the ENQUOTE_NAME formatted String for the SQL name If the Oracle JDBC is present, use the new OracleStatement.enquoteIdentifier API in the JDK8 JDBC.                                             |
    | `static java.lang.String`                 | `enquoteNameSQLName``(java.sql.Connection conn, java.lang.String name, boolean capitalize)`<br>Returns the ENQUOTE_NAME formatted String for the SQL name use the DBMS_ASSERT.ENQUOTE_NAME formatted String for the SQL name This method is added due to avoid SQL Injection issues. |
    | `static java.lang.String`                 | `enquoteTableName``(java.sql.Connection conn, java.lang.String tableName)`<br>Enquotes a table name with or without schema name which is separated by ".".                                                                                                                           |
    | `static java.lang.String`                 | `getConnStr``(java.lang.String mode, java.lang.String host, java.lang.String port, java.lang.String sid)`<br>connects to the database using supplied information.                                                                                                                    |
    | `static java.lang.String`                 | `getDBVersion``(java.sql.Connection conn)`<br>Gets the version of the database connected.                                                                                                                                                                                            |
    | `static java.lang.String`                 | `getJDBCDriverVersion``(java.sql.Connection conn)`<br>Gets the oracle JDBC driver version string.                                                                                                                                                                                    |
    | `static java.awt.Shape`                   | `getShape``(double[] coords, boolean close)`<br>converts the coordinate array into a GeneralPath shape.                                                                                                                                                                              |
    | `static boolean`                          | `isGeodetic``(int srid)`<br>Using an Oracle convention to determin if a srid is geodetic.                                                                                                                                                                                            |
    | `static boolean`                          | `isPre9i``(java.sql.Connection conn)`<br>Determin if a database is pre-9i version.                                                                                                                                                                                                   |
    | `static void`                             | `main``(java.lang.String[] args)`                                                                                                                                                                                                                                                    |
    | `static java.awt.geom.Rectangle2D.Double` | `mbr``(double[] coords)`                                                                                                                                                                                                                                                             |
    | `static java.lang.String`                 | `qualifiedSQLName``(java.sql.Connection conn, java.lang.String name)`<br>Checks if the specified name is a qualified SQL name.                                                                                                                                                       |
    | `static byte[]`                           | `readFile``(java.lang.String f)`                                                                                                                                                                                                                                                     |
    | `static java.util.ArrayList`              | `splitBy``(java.lang.String str, java.lang.String delim)`<br>gets an array list of strings that are separated by delimiters such as commas                                                                                                                                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Util

          public Util()

  <!-- -->

  - ### Method Detail

    - #### convert

          public static double[] convert(java.lang.String str)

      Converts a string of coordinates into a double array. The delimiter between the numbers can be white space, comma, semicolon, or CR.

    <!-- -->

    - #### splitBy

          public static java.util.ArrayList splitBy(java.lang.String str,
                                                    java.lang.String delim)

      gets an array list of strings that are separated by delimiters such as commas
      Parameters:
      `str` - the input string to be tokenized

      `delim` - the delimiter to be used in tokenizing the string

      Returns:
      ArrayList of all the tokens

    <!-- -->

    - #### getShape

          public static java.awt.Shape getShape(double[] coords,
                                                boolean close)

      converts the coordinate array into a GeneralPath shape.

    <!-- -->

    - #### mbr

          public static java.awt.geom.Rectangle2D.Double mbr(double[] coords)

    <!-- -->

    - #### readFile

          public static byte[] readFile(java.lang.String f)
                                 throws java.io.IOException

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### connect

          public static java.sql.Connection connect(java.lang.String host,
                                                    java.lang.String sid,
                                                    java.lang.String port,
                                                    java.lang.String user,
                                                    java.lang.String passwd,
                                                    java.lang.String mode,
                                                    int rowPref)

      Establishes an Oracle JDBC connection to the specified database. If a OCI mode connection is requested but failed, then a "thin" JDBC connection is automatically attempted.
      Parameters:
      `host` - name of the host machine where the database runs

      `sid` - instance id of the database

      `port` - which port the database is listening at

      `user` - the database user to connect to

      `passwd` - the database user's password

      `mode` - the connection mode; possible values are "thin", "oci" or "oci8". If null value is supplied the default "oci8" mode is attempted.

      `rowPref` - the row prefetch to be set with the connection. If a value less than or equal to zero is supplied, the defualt value of 32 will be used for this connection.

      Returns:
      an Oracle JDBC connection if successful, otherwise null.

    <!-- -->

    - #### getJDBCDriverVersion

          public static java.lang.String getJDBCDriverVersion(java.sql.Connection conn)

      Gets the oracle JDBC driver version string.

    <!-- -->

    - #### getDBVersion

          public static java.lang.String getDBVersion(java.sql.Connection conn)

      Gets the version of the database connected.

    <!-- -->

    - #### isPre9i

          public static boolean isPre9i(java.sql.Connection conn)

      Determin if a database is pre-9i version. This is internal.

    <!-- -->

    - #### isGeodetic

          public static boolean isGeodetic(int srid)

      Using an Oracle convention to determin if a srid is geodetic. This is internal.

    <!-- -->

    - #### getConnStr

          public static java.lang.String getConnStr(java.lang.String mode,
                                                    java.lang.String host,
                                                    java.lang.String port,
                                                    java.lang.String sid)

      connects to the database using supplied information. If any one of the following parameters are null, then the connection will be made to a (default) local database instance.
             mode, host, port, sid


      If user requires OCI-mode connection but failed, then a "Thin" mode connection is automatically attempted.
      Parameters:
      `mode` - the mode of connection. It could either be a THIN or an OCI connection. THIN is slower but pure java, while OCI is faster but requires Oracle OCI library.

      `host` - the host where the database is located.

      `port` - the port where the database instance listens (default is 1521)

      `sid` - the instance id of the database.

      Returns:
      a JDBC connection to specified Oracle Database. This is internal.

    <!-- -->

    - #### center

          public static void center(java.awt.Component c)

      Centers an awt component w.r.t. the screen.

    <!-- -->

    - #### main

          public static void main(java.lang.String[] args)
                           throws java.io.IOException,
                                  java.lang.Exception,
                                  java.sql.SQLException

      Throws:
      `java.io.IOException`

      `java.lang.Exception`

      `java.sql.SQLException`

    <!-- -->

    - #### checkSQLName

          public static java.lang.String checkSQLName(java.lang.String string,
                                                      int maxStringLength)
                                               throws java.sql.SQLException

      Checks for any illegal characters in a SQL name. Only alpha-numeric characters and ".", "\_","\$","#" are allowed.
      Parameters:
      `string` - input string

      `maxStringLength` - maximum length for input string

      Returns:
      string Retruns the string if passes the check

      Throws:
      `java.sql.SQLException` - An exception is thrown if the input string contains any illegal characters or exceeds the maximum length

    <!-- -->

    - #### checkSQLName

          public static java.lang.String checkSQLName(java.lang.String string,
                                                      int maxStringLength,
                                                      Util.CheckType checkType)
                                               throws java.sql.SQLException

      Checks: - for any illegal characters in a SQL name. Only alpha-numeric characters and ".", "\_","\$","#" are allowed. - for any illegal characters in a SQL Column Data Type name. Only alpha-numeric characters and ".", "\_","\$","#","(",")","-",":"," " are allowed; but "--" not allowed. - for any illegal characters in a URL. Rules are from java.net.URL.
      Parameters:
      `string` - input string

      `maxStringLength` - maximum length for input string

      `checkType` - sqlName, URL or SQLType

      Returns:
      string Retruns the string if passes the check

      Throws:
      `java.sql.SQLException` - An exception is thrown if the input string contains any illegal characters or exceeds the maximum length

    <!-- -->

    - #### qualifiedSQLName

          public static java.lang.String qualifiedSQLName(java.sql.Connection conn,
                                                          java.lang.String name)
                                                   throws java.sql.SQLException

      Checks if the specified name is a qualified SQL name. It calls SYS.DBMS_ASSERT.qualified_sql_name function.
      Parameters:
      `conn` - the database connection

      `name` - the input name

      Returns:
      string Retruns the string if passes the check

      Throws:
      `java.sql.SQLException` - A SQLexception is thrown if the dbms_assert.qualified_sql_name failed

    <!-- -->

    - #### enquoteNameSQLName

          public static java.lang.String enquoteNameSQLName(java.sql.Connection conn,
                                                            java.lang.String name)
                                                     throws java.sql.SQLException

      Returns the ENQUOTE_NAME formatted String for the SQL name If the Oracle JDBC is present, use the new OracleStatement.enquoteIdentifier API in the JDK8 JDBC. Otherwise use the DBMS_ASSERT.ENQUOTE_NAME formatted String for the SQL name using "false" for the second parameter (i.e., no capitalization of SQL name). This method is added due to avoid SQL Injection issues.
      Parameters:
      `conn` - the database connection

      `name` - the input name

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### enquoteNameSQLName

          public static java.lang.String enquoteNameSQLName(java.sql.Connection conn,
                                                            java.lang.String name,
                                                            boolean capitalize)
                                                     throws java.sql.SQLException

      Returns the ENQUOTE_NAME formatted String for the SQL name use the DBMS_ASSERT.ENQUOTE_NAME formatted String for the SQL name This method is added due to avoid SQL Injection issues.
      Parameters:
      `conn` - the database connection

      `name` - the input name

      `capitalize` - If TRUE, alphabetic characters of str which was not in quotes are translated to upper case

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### enquoteTableName

          public static java.lang.String enquoteTableName(java.sql.Connection conn,
                                                          java.lang.String tableName)
                                                   throws java.sql.SQLException

      Enquotes a table name with or without schema name which is separated by ".". This method also can be used to enquote all column names, including object column names like col.attr1.attr2.attr3 == "COL"."ATTR1"."ATTR2"."ATTR3" and "col".attr1."attr2".attr3 == "col"."ATTR1"."attr2"."ATTR3"
      Parameters:
      `conn` -

      `tableName` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### enquoteColumnName

          public static java.lang.String enquoteColumnName(java.sql.Connection conn,
                                                           java.lang.String columnName)
                                                    throws java.sql.SQLException

      Enquotes a column name.
      Parameters:
      `conn` -

      `columnName` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](TIN2Contours.md)
- [Next Class](Util.CheckType.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
