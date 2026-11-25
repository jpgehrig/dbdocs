A call specification and the Java method it publishes must reside in the same schema, unless the Java method has a `PUBLIC` synonym. You can declare the call specification as a:

- Standalone PL/SQL function or procedure

- Packaged PL/SQL function or procedure

- Member method of a SQL object type

A call specification exposes the top-level entry point of a Java method to Oracle Database. As a result, you can publish only `public` `static` methods. However, there is an exception. You can publish instance methods as member methods of a SQL object type.

Packaged call specifications perform as well as top-level call specifications. As a result, to ease maintenance, you may want to place call specifications in a package body. This will help you to modify call specifications without invalidating other schema objects. Also, you can overload the call specifications.

This section covers the following topics:

- About Setting Parameter Modes

- About Mapping Data Types

- Using the Server-Side Internal JDBC Driver

### 6.2.1 About Setting Parameter Modes

In Java and other object-oriented languages, a method cannot assign values to objects passed as arguments. When calling a method from SQL or PL/SQL, to change the value of an argument, you must declare it as an `OUT` or `IN OUT` parameter in the call specification. The corresponding Java parameter must be an array with only one element.

You can replace the element value with another Java object of the appropriate type, or you can modify the value, if the Java type permits. Either way, the new value propagates back to the caller. For example, you map a call specification `OUT` parameter of the `NUMBER` type to a Java parameter declared as `float[]` `p`, and then assign a new value to `p[0]`.

**Note:**

A function that declares `OUT` or `IN`` OUT` parameters cannot be called from SQL data manipulation language (DML) statements.

### 6.2.2 About Mapping Data Types

In a call specification, the corresponding SQL and Java parameters and function results must have compatible data types.

Table 6-1 lists the legal data type mappings. Oracle Database converts between the SQL types and Java classes automatically.

Table 6-1 Legal Data Type Mappings

| SQL Type                             | Java Class                                                                                                                                                                                                                                                                     |
|:-------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CHAR`, `VARCHAR2`, `LONG`           | `java.lang.String`<br>`oracle.sql.CHAR`<br>`oracle.sql.ROWID`<br>`byte[]`                                                                                                                                                                                                      |
| `NUMBER`                             | `boolean`<br>`char`<br>`byte`<br>`byte[]`<br>`short`<br>`int`<br>`long`<br>`float`<br>`double`<br>`java.lang.Byte`<br>`java.lang.Short`<br>`java.lang.Integer`<br>`java.lang.Long`<br>`java.lang.Float`<br>`java.lang.Double`<br>`java.math.BigDecimal`<br>`oracle.sql.NUMBER` |
| `BINARY_INTEGER`                     | `boolean`<br>`char`<br>`byte`<br>`byte[]`<br>`short`<br>`int`<br>`long`                                                                                                                                                                                                        |
| `BINARY_FLOAT`                       | `oracle.sql.BINARY_FLOAT`<br>`byte[]`                                                                                                                                                                                                                                          |
| `BINARY_DOUBLE`                      | `oracle.sql.BINARY_DOUBLE`<br>`byte[]`                                                                                                                                                                                                                                         |
| `DATE`                               | `oracle.sql.DATE`<br>`byte[]`                                                                                                                                                                                                                                                  |
| `RAW`                                | `oracle.sql.RAW`<br>`byte[]`                                                                                                                                                                                                                                                   |
| `BLOB`                               | `oracle.sql.BLOB`                                                                                                                                                                                                                                                              |
| `CLOB`                               | `oracle.sql.CLOB`                                                                                                                                                                                                                                                              |
| `BFILE`                              | `oracle.sql.BFILE`                                                                                                                                                                                                                                                             |
| `ROWID`                              | `oracle.sql.ROWID`<br>`byte[]`                                                                                                                                                                                                                                                 |
| `TIMESTAMP`                          | `oracle.sql.TIMESTAMP`<br>`byte[]`                                                                                                                                                                                                                                             |
| `TIMESTAMP WITH TIME ZONE`           | `oracle.sql.TIMESTAMPTZ`                                                                                                                                                                                                                                                       |
| `TIMESTAMP WITH LOCAL TIME ZONE`     | `oracle.sql.TIMESTAMPLTZ`                                                                                                                                                                                                                                                      |
| ref cursor                           | j`ava.sql.ResultSet`<br>`sqlj.runtime.ResultSetIterator`                                                                                                                                                                                                                       |
| user defined named types, ADTs       | `oracle.sql.STRUCT`                                                                                                                                                                                                                                                            |
| opaque named types                   | `oracle.sql.OPAQUE`                                                                                                                                                                                                                                                            |
| nested tables and VARRAY named types | `oracle.sql.ARRAY`                                                                                                                                                                                                                                                             |
| references to named types            | `oracle.sql.REF`                                                                                                                                                                                                                                                               |

You also must consider the following:

- The last four SQL types are collectively referred to as named types.

- All SQL types except `BLOB`, `CLOB`, `BFILE`, `REF` `CURSOR`, and the named types can be mapped to the Java type `byte[]`, which is a Java byte array. In this case, the argument conversion means copying the raw binary representation of the SQL value to or from the Java byte array.

- Java classes that implement the `ORAData` interface and related methods, or Java classes that are subclasses of the `oracle.sql` classes appearing in the table, can be mapped from SQL types other than `BINARY_INTEGER` and `REF` `CURSOR`.

- The `UROWID` type and the `NUMBER` subtypes, such as `INTEGER` and `REAL`, are not supported.

- A value larger than 32 KB cannot be retrieved from a `LONG` or `LONG RAW` column into a Java stored procedure.

### 6.2.3 Using the Server-Side Internal JDBC Driver

Java Database Connectivity (JDBC) enables you establish a connection to the database using the `DriverManager` class, which manages a set of JDBC drivers. You can use the `getConnection()` method after loading the JDBC drivers. When the `getConnection()` method finds the right driver, it returns a `Connection` object that represents a database session. All SQL statements are run within the context of that session.

However, the server-side internal JDBC driver runs within a default session and a default transaction context. As a result, you are already connected to the database, and all your SQL operations are part of the default transaction. You need not register the driver because it comes preregistered. To get a `Connection` object, run the following line of code:

    Connection conn = DriverManager.getConnection("jdbc:default:connection:");

Use the `Statement` class for SQL statements that do not take `IN` parameters and are run only once. When called on a `Connection` object, the `createStatement()` method returns a new `Statement` object, as follows:

    String sql = "DROP " + object_type + " " + object_name;
    Statement stmt = conn.createStatement();
    stmt.executeUpdate(sql);

Use the `PreparedStatement` class for SQL statements that take `IN` parameters or are run more than once. The SQL statement, which can contain one or more parameter placeholders, is precompiled. A question mark (?) serves as a placeholder. When called on a `Connection` object, the `prepareStatement()` method returns a new `PreparedStatement` object, which contains the precompiled SQL statement. For example:

    String sql = "DELETE FROM dept WHERE deptno = ?";
    PreparedStatement pstmt = conn.prepareStatement(sql);
    pstmt.setInt(1, deptID);
    pstmt.executeUpdate();

A `ResultSet` object contains SQL query results, that is, the rows that meet the search condition. You can use the `next()` method to move to the next row, which then becomes the current row. You can use the `get``XXX``()` methods to retrieve column values from the current row. For example:

    String sql = "SELECT COUNT(*) FROM " + tabName;
    int rows = 0;
    Statement stmt = conn.createStatement();
    ResultSet rset = stmt.executeQuery(sql);
    while (rset.next())
    {
      rows = rset.getInt(1);
    }

A `CallableStatement` object lets you call stored procedures. It contains the call text, which can include a return parameter and any number of `IN`, `OUT`, and `IN OUT` parameters. The call is written using an escape clause, which is delimited by braces (`{}`). As the following examples show, the escape syntax has three forms:

    // parameterless stored procedure
    CallableStatement cstmt = conn.prepareCall("{CALL proc}");

    // stored procedure
    CallableStatement cstmt = conn.prepareCall("{CALL proc(?,?)}");

    // stored function
    CallableStatement cstmt = conn.prepareCall("{? = CALL func(?,?)}");

#### Important Points

When developing JDBC applications that access stored procedures, you must consider the following:

- Each Oracle JVM session has a single implicit native connection to the Database session in which it exists. This connection is conceptual and is not a Java object. It is an inherent aspect of the session and cannot be opened or closed from within the JVM.

- The server-side internal JDBC driver runs within a default transaction context. You are already connected to the database, and all your SQL operations are part of the default transaction. Note that this transaction is a local transaction and not part of a global transaction, such as that implemented by Java Transaction API (JTA) or Java Transaction Service (JTS).

- Statements and result sets persist across calls and their finalizers do not release database cursors. To avoid running out of cursors, close all statements and result sets after you have finished using them. Alternatively, you can ask your DBA to raise the limit set by the initialization parameter, `OPEN_CURSORS`.

- The server-side internal JDBC driver does not support auto-commits. As a result, your application must explicitly commit or roll back database changes.

- You cannot connect to a remote database using the server-side internal JDBC driver. You can connect only to the server running your Java program. For server-to-server connections, use the server-side JDBC Thin driver. For client/server connections, use the client-side JDBC Thin or JDBC Oracle Call Interface (OCI) driver.

- Typically, you should not close the default connection instance because it is a single instance that can be stored in multiple places, and if you close the instance, each would become unusable. If it is closed, a later call to the `OracleDriver.defaultConnection` method gets a new, open instance. The `OracleDataSource.getConnection` method returns a new object every time you call it, but, it does not create a new database connection every time. They all utilize the same implicit native connection and share the same session state, in particular, the local transaction.

**See Also:**

[Oracle Database JDBC Developer’s Guide](../jjdbc/introducing-JDBC.md)
