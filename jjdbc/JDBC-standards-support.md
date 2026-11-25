Oracle Java Database Connectivity (JDBC) drivers support different versions of the JDBC standard features. In Oracle Database 12c Release 2 (12.2.0.1), Oracle JDBC drivers have been enhanced to provide support for the JDBC 4.1 standards. These features are provided through the `oracle.jdbc` and `oracle.sql` packages. These packages support Java Development Kit (JDK) release 8. This chapter discusses the JDBC standards support in Oracle JDBC drivers. It contains the following sections:

- Support for JDBC 2.0 Standard

- Support for JDBC 3.0 Standard

- Support for JDBC 4.0 Standard

- Support for JDBC 4.1 Standard

- Support for JDBC 4.2 Standard

### 3.1 Support for JDBC 2.0 Standard

This release of Oracle JDBC drivers provide support for JDBC 2.0 features through JDK 1.2 and later versions. There are three areas to consider:

- Support for data types, such as objects, arrays, and large objects (LOBs), which is handled through the `java.sql` package.

- Support for standard features, such as result set enhancements and update batching, which is handled through standard objects, such as `Connection`, `ResultSet`, and `PreparedStatement`, under JDK 1.2.x and later.

- Support for extended features, such as features of the JDBC 2.0 optional package, also known as the standard extension application programming interface (API), including data sources, connection pooling, and distributed transactions.

This section covers the following topics:

- Data Type Support

- Standard Feature Support

- Extended Feature Support

- Standard versus Oracle Performance Enhancement APIs

**Note:**

Versions of JDK earlier than 5.0 are no longer supported. The package `oracle.jdbc2` has been removed.

#### 3.1.1 Data Type Support

Oracle JDBC fully supports JDK 6 and JDK 7, which includes standard JDBC 2.0 functionality through implementation of interfaces in the standard `java.sql` package. These interfaces are implemented as appropriate by classes in the `oracle.sql` and `oracle.jdbc` packages.

#### 3.1.2 Standard Feature Support

In a JDK 6.0 environment, using the JDBC classes in `ojdbc6.jar`, JDBC 2.0 features, such as scrollable result sets, updatable result sets, and update batching, are supported through methods specified by standard JDBC 2.0 interfaces.

#### 3.1.3 Extended Feature Support

Features of the JDBC 2.0 optional package, including data sources, connection pooling, and distributed transactions, are supported in a JDK 1.2.x or later environment.

The standard `javax.sql` package and classes that implement its interfaces are included in the Java Archive (JAR) files packaged with Oracle Database.

#### 3.1.4 Standard versus Oracle Performance Enhancement APIs

Fetch size or row prefetching is available under JDBC 2.0, which had previously been available only as an Oracle extension. You have the option of using the standard model or the Oracle model. Oracle recommends that you use the JDBC standard model whenever possible. Do not, however, try to mix usage of the standard model and Oracle model within a single application for this feature.

**Related Topics**

- [Row Fetch Size](resultset.md)

### 3.2 Support for JDBC 3.0 Standard

Oracle Database 12c Release 1 JDBC drivers provide support for Standard JDBC 3.0 features through JDK 1.4 and later versions. The following table lists the JDBC 3.0 features supported by this release of Oracle JDBC drivers and gives references to a detailed discussion of each feature.

Table 3-1 Key Areas of JDBC 3.0 Functionality

| Feature                                         | Comments and References                                                                                                                                                                                                        |
|:------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Transaction savepoints                          | See "Overview of Transaction Savepoints" for information.                                                                                                                                                                      |
| Statement caching                               | Reuse of prepared statements by connection pools. See [Statement and Result Set Caching](statement-and-resultset-caching.md) .                                                                                                 |
| Switching between local and global transactions | See "[About Switching Between Global and Local Transactions](distributed-transactions.md)".                                                                                                                                    |
| LOB modification                                | See "JDBC 3.0 LOB Interface Methods" JDBC 3.0 LOB Interface Methods.                                                                                                                                                           |
| Named SQL parameters                            | See "[Interface oracle.jdbc.OracleCallableStatement](Oracle-extensions.md)" and "[Interface oracle.jdbc.OraclePreparedStatement](Oracle-extensions.md)" [Interface oracle.jdbc.OraclePreparedStatement](Oracle-extensions.md). |
| RowSets                                         | See [JDBC RowSets](JDBC-Rowsets.md)                                                                                                                                                                                            |
| Retrieving auto-generated keys                  | See "Retrieval of Auto-Generated Keys" Retrieval of Auto-Generated Keys                                                                                                                                                        |
| Result set holdability                          | See "Result Set Holdability" Result Set Holdability                                                                                                                                                                            |

The following JDBC 3.0 features supported by Oracle JDBC drivers are covered in this section:

- Overview of Transaction Savepoints

- Retrieval of Auto-Generated Keys

- JDBC 3.0 LOB Interface Methods

- Result Set Holdability

#### 3.2.1 Overview of Transaction Savepoints

The JDBC 3.0 specification supports savepoints, which offer finer demarcation within transactions. Applications can set a savepoint within a transaction and then roll back all work done after the savepoint. Savepoints relax the atomicity property of transactions. A transaction with a savepoint is atomic in the sense that it appears to be a single unit outside the context of the transaction, but code operating within the transaction can preserve partial states.

**Note:**

Savepoints are supported for local transactions only. Specifying a savepoint within a global transaction causes a `SQLException` exception to be thrown.

##### 3.2.1.1 About Creating a Savepoint

You create a savepoint using the `Connection.setSavepoint` method, which returns a `java.sql.Savepoint` instance.

A savepoint is either named or unnamed. You specify the name of a savepoint by supplying a string to the `setSavepoint` method. If you do not specify a name, then the savepoint is assigned an integer ID. You retrieve a name using the `getSavepointName` method. You retrieve an ID using the `getSavepointId` method.

**Note:**

Attempting to retrieve a name from an unnamed savepoint or attempting to retrieve an ID from a named savepoint throws a `SQLException` exception.

##### 3.2.1.2 About Rolling Back to a Savepoint

You roll back to a savepoint using the `Connection.rollback(Savepoint svpt)` method. If you try to roll back to a savepoint that has been released, then a `SQLException` exception is thrown.

##### 3.2.1.3 About Releasing a Savepoint

You remove a savepoint using the` Connection.releaseSavepoint(Savepoint svpt)` method.

##### 3.2.1.4 About Checking Savepoint Support

You query if savepoints are supported by your database by calling the `oracle.jdbc.OracleDatabaseMetaData.supportsSavepoints` method, which returns `true` if savepoints are available, `false` otherwise.

##### 3.2.1.5 Savepoint Notes

When using savepoints, you must consider the following:

- After a savepoint has been released, attempting to reference it in a rollback operation will cause a `SQLException` exception to be thrown.

- When a transaction is committed or rolled back, all savepoints created in that transaction are automatically released and become invalid.

- Rolling a transaction back to a savepoint automatically releases and makes invalid any savepoints created after the savepoint in question.

#### 3.2.2 Retrieval of Auto-Generated Keys

Many database systems automatically generate a unique key field when a row is inserted. Oracle Database provides the same functionality with the help of sequences and triggers. JDBC 3.0 introduces the retrieval of auto-generated keys feature that enables you to retrieve such generated values. In JDBC 3.0, the following interfaces are enhanced to support the retrieval of auto-generated keys feature:

- `java.sql.DatabaseMetaData`

- `java.sql.Connection`

- `java.sql.Statement`

These interfaces provide methods that support retrieval of auto-generated keys. However, this feature is supported only when `INSERT` statements are processed. Other data manipulation language (DML) statements are processed, but without retrieving auto-generated keys.

**Note:**

The Oracle server-side internal driver does not support the retrieval of auto-generated keys feature.

##### 3.2.2.1 java.sql.Statement

If key columns are not explicitly indicated, then Oracle JDBC drivers cannot identify which columns need to be retrieved. When a column name or column index array is used, Oracle JDBC drivers can identify which columns contain auto-generated keys that you want to retrieve. However, when the `Statement.RETURN_GENERATED_KEYS` integer flag is used, Oracle JDBC drivers cannot identify these columns. When the integer flag is used to indicate that auto-generated keys are to be returned, the `ROWID` pseudo column is returned as key. The `ROWID` can be then fetched from the `ResultSet` object and can be used to retrieve other columns.

##### 3.2.2.2 Sample Code

The following code illustrates retrieval of auto-generated keys:

    /** SQL statements for creating an ORDERS table and a sequence for generating the
      * ORDER_ID.
      *
      * CREATE TABLE ORDERS (ORDER_ID NUMBER, CUSTOMER_ID NUMBER, ISBN NUMBER,
      * DESCRIPTION NCHAR(5))
      *
      * CREATE SEQUENCE SEQ01 INCREMENT BY 1 START WITH 1000
      */

    ...
    String cols[] = {"ORDER_ID", "DESCRIPTION"};

    // Create a PreparedStatement for inserting a row into the ORDERS table.
    OraclePreparedStatement pstmt = (OraclePreparedStatement)
    conn.prepareStatement("INSERT INTO ORDERS (ORDER_ID, CUSTOMER_ID, ISBN,  DESCRIPTION) VALUES (SEQ01.NEXTVAL, 101,
     966431502, ?)", cols);
    char c[] = {'a', '\u5185', 'b'};
    String s = new String(c);

    pstmt.setNString(1, s);
    pstmt.executeUpdate();
    ResultSet rset = pstmt.getGeneratedKeys();
    ...

In the preceding example, a sequence, `SEQ01`, is created to generate values for the `ORDER_ID` column starting from `1000` and incrementing by `1` each time the sequence is processed to generate the next value. An `OraclePreparedStatement` object is created to insert a row in to the `ORDERS` table.

##### 3.2.2.3 Limitations of Auto-Generated Keys

Auto-generated keys are implemented using the DML returning clause. So, you need to access the `ResultSet` object returned from `getGeneratedKeys` method by position only and no bind variable names should be used as columns in the `ResultSet` object.

#### 3.2.3 JDBC 3.0 LOB Interface Methods

The following tables show the conversions between Oracle proprietary methods and JDBC 3.0 standard methods.

Table 3-2 BLOB Method Equivalents

| Oracle Proprietary Method                       | JDBC 3.0 Standard Method                                |
|:------------------------------------------------|:--------------------------------------------------------|
| `putBytes(long pos, byte [] bytes)`             | `setBytes(long pos, byte[] bytes) `                     |
| `putBytes(long pos, byte [] bytes, int length)` | `setBytes(long pos, byte[] bytes, int offset, int len)` |
| `getBinaryOutputStream(long pos)`               | `setBinaryStream(long pos)`                             |
| `trim (long len)`                               | `truncate(long len)`                                    |

Table 3-3 CLOB Method Equivalents

| Oracle Proprietary Method            | JDBC 3.0 Standard Method                               |
|:-------------------------------------|:-------------------------------------------------------|
| `putString(long pos, String str)`    | `setString(long pos, String str) `                     |
| not applicable                       | `setString(long pos, String str, int offset, int len)` |
| `getAsciiOutputStream(long pos) `    | `setAsciiStream(long pos)`                             |
| `getCharacterOutputStream(long pos)` | `setCharacterStream(long pos)`                         |
| `trim (long len)`                    | `truncate(long len)`                                   |

#### 3.2.4 Result Set Holdability

Result set holdability was introduced since JDBC 3.0. This feature enables applications to decide whether the `ResultSet` objects should be open or closed, when a commit operation is performed. The commit operation could be either implicit or explicit.

Oracle Database supports only `HOLD_CURSORS_OVER_COMMIT`. Therefore, it is the default value for Oracle JDBC drivers. Any attempt to change holdability will throw a `SQLFeatureNotSupportedException` exception.

### 3.3 Support for JDBC 4.0 Standard

Oracle Database Release 18c JDBC drivers provide support for the JDBC 4.0 standard.

**Note:**

The JDBC 4.0 specification defines the `java.sql.Connection.createArrayOf` factory method to create `java.sql.Array` objects. The `createArrayOf` method accepts the name of the array element type as one of the arguments, where the array type is anonymous. Oracle database supports only named array types, not anonymous array types. So, the current release of Oracle JDBC drivers do not and cannot support the `createArrayOf` method. You must use the Oracle specific `createARRAY` method to create an array type.

**See Also:**

- "[Creating ARRAY Objects](Oracle-collections.md)" for more information about the `createArrayOf` method.

- The following page for detailed information about these features as this document provides only an overview of these new features

  <http://docs.oracle.com/javase/6/docs/>

Some of the features available in Oracle Database Release 18c JDBC drivers are the following:

- Wrapper Pattern Support

- SQLXML Type

- Enhanced Exception Hierarchy and SQLException

- The RowId Data Type

- LOB Creation

- National Language Character Set Support

#### 3.3.1 Wrapper Pattern Support

Wrapper pattern is a common coding pattern used in Java applications to provide extensions beyond the traditional JDBC API that are specific to a data source. You may need to use these extensions to access the resources that are wrapped as proxy class instances representing the actual resources. JDBC 4.0 introduces the `Wrapper` interface that describes a standard mechanism to access these wrapped resources represented by their proxy, to permit direct access to the resource delegates.

The `Wrapper` interface provides the following two methods:

- `public boolean isWrapperFor(Class<?> iface) throws SQLException;`

- `public <T> T unwrap(Class<T> iface) throws SQLException;`

The other JDBC 4.0 interfaces, except those that represent SQL data, all implement this interface. These include `Connection`, `Statement` and its subtypes, `ResultSet`, and the metadata interfaces.

**See Also:**

[`http://docs.oracle.com/javase/7/docs/api/java/sql/Wrapper.html`](http://docs.oracle.com/javase/7/docs/api/java/sql/Wrapper.html)

#### 3.3.2 SQLXML Type

One of the most important updates in JDBC 4.0 standard is the support for the XML data type, defined by the SQL 2003 standard. Now JDBC offers a mapping interface to support the SQL/XML database data type, that is, `java.sql.SQLXML`. This new JDBC interface defines Java native bindings for XML, thus making handling of any database XML data easier and more efficient.

**Note:**

- You also need to include the `xdb6.jar` and `xmlparserv2.jar` files in the `classpath` environment variable to use `SQLXML` type data, if they are not already present in the `classpath`.

- SQLXML is not supported in `CachedRowset` objects.

You can create an instance of XML by calling the `createSQLXML` method in `java.sql.Connection` interface. This method returns an empty XML object.

The `PreparedStatement`, `CallableStatement`, and `ResultSet` interfaces have been extended with the appropriate getter and setter methods in the following way:

- `PreparedStatement`: The method `setSQLXML` have been added

- `CallableStatement`: The methods `getSQLXML` and `setSQLXML` have been added

- `ResultSet`: The method `getSQLXML` have been added

**Note:**

In Oracle Database 10g and earlier versions of Oracle Database 11g, Oracle JDBC drivers supported the Oracle SQL XML type (XMLType) through an Oracle proprietary extension, which did not conform to the JDBC standard.

The 11.2.0.2 Oracle JDBC drivers conformed to the JDBC standard with the introduction of a new connection property, `oracle.jdbc.getObjectReturnsXMLType`. If you set this property to `false`, then the `getObject` method returns an instance of `java.sql.SQLXML` type and if you depend on the existing Oracle proprietary support for SQL XMLType using `oracle.xdb.XMLType`, then you can change the value of this property back to `true`.

However, setting of the `getObjectReturnsXMLType` property is not required for the current version of Oracle JDBC drivers.

##### Example

Example 3-1 Accessing SQLXML Data

The following example shows how to create an instance of XML from a `String`, write the XML data into the Database, and then retrieve the XML data from the Database.

    import java.sql.*;
    import java.util.Properties;
    import oracle.jdbc.pool.OracleDataSource;

    public class SQLXMLTest
     {

      public static void main(String[] args)
      {

      Connection conn = null;
      Statement stmt = null;
      ResultSet rs = null;
      PreparedStatement ps = null;

      String xml = "<?xml version=\"1.0\"?>\n" +
        "<oldjoke>\n" +
        "<burns>Say <quote>goodnight</quote>, Gracie.</burns>\n" +
        "<allen><quote>Goodnight, Gracie.</quote></allen>\n" +
        "<applause/>\n" +
        "</oldjoke>";

      try
      {

         OracleDataSource ods = new OracleDataSource();
         ods.setURL("jdbc:oracle:thin:@//localhost:5221/orcl");
         ods.setUser("HR");
         ods.setPassword("hr");
         conn = ods.getConnection();

         ps = conn.prepareStatement("insert into x values (?, ?)");
         ps.setString(1, "string to string");
         SQLXML x = conn.createSQLXML();
         x.setString(xml);
         ps.setSQLXML(2, x);
         ps.execute();
         stmt = conn.createStatement();
         rs = stmt.executeQuery("select * from x");
         while (rs.next())
         {
           x = rs.getSQLXML(2);
           System.out.println(rs.getString(1) + "\n" + rs.getSQLXML(2).getString());
           x.free();
         }

         rs.close();
         ps.close();
      }

      catch (SQLException e){e.printStackTrace ();}

      }
    }

**Note:**

Calling a setter method with an empty XML throws `SQLException`. The getter methods never return an empty XML.

#### 3.3.3 Enhanced Exception Hierarchy and SQLException

JDBC 3.0 defines only a single exception, `SQLException`. However, there are large categories of errors and it is useful to distinguish them. This feature provides subclasses of the `SQLException` class to identify the different categories of errors. The primary distinction is between permanent errors and transient errors. Permanent errors are a result of the correct operation of the system and will always occur. Transient errors are the result of failures, including timeouts, of some part of the system and may not reoccur.

JDBC 4.0 adds additional exceptions to represent transient and permanent errors and the different categories of these errors.

Also, the `SQLException` class and its subclasses are enhanced to provide support for the J2SE chained exception functionality.

#### 3.3.4 The RowId Data Type

JDBC 4.0 provides the `java.sql.RowId` data type to represent SQL `ROWID` values. You can retrieve a `RowId` value using the getter methods defined in the `ResultSet` and `CallableStatement` interfaces. You can also use a `RowId` value in a parameterized `PreparedStatement` to set a parameter with a `RowId` object or in an updatable result set to update a column with a specific `RowId` value.

A `RowId` object is valid until the identified row is not deleted. A `RowId` object may also be valid for the following:

- The duration of the transaction in which it is created

- The duration of the session in which it is created

- An undefined duration where by it is valid forever

The lifetime of the RowId object can be determined by calling the `DatabaseMetaData.getRowIdLifetime` method.

#### 3.3.5 LOB Creation

In JDBC 4.0, the `Connection` interface has been enhanced to provide support for the creation of `BLOB`, `CLOB`, and `NCLOB` objects. The interface provides the `createBlob`, `createClob`, and `createNClob` methods that enable you to create `Blob`, `Clob`, and `NClob` objects.

The created large objects (LOBs) do not contain any data. You can add or retrieve data to or from these objects by calling the APIs available in the `java.sql.Blob`, `java.sql.Clob`, and `java.sql.NClob` interfaces. You can either retrieve the entire content or a part of the content from these objects. The following code snippet illustrates how to retrieve 100 bytes of data from a `BLOB` object starting at offset 200:

    ...
    Connection con = DriverManager.getConnection(url, props);
    Blob aBlob = con.createBlob();
    // Add data to the BLOB object.
    aBlob.setBytes(...);
    ...
    // Retrieve part of the data from the BLOB object.
    InputStream is = aBlob.getBinaryStream(200, 100);
    ...

You can also pass LOBs as input parameters to a `PreparedStatement` object by using the `setBlob`, `setClob`, and `setNClob` methods. You can use the `updateBlob`, `updateClob`, and `updateNClob` methods to update a column value in an updatable result set.

These LOBs are temporary LOBs and can be used for any purpose for which temporary LOBs should be used. To make the storage permanent in the database, these LOBs must be written to a table.

**See Also:**

"[About Working With Temporary LOBs](LOBs-and-BFiles.md)"

Temporary LOBs remain valid for at least the duration of the transaction in which they are created. This may result in unwarranted use of memory during a long running transaction. You can release LOBs by calling their `free` method, as follows:

    ...
    Clob aClob = con.createClob();
    int numWritten = aClob.setString(1, val);
    aClob.free();
    ...

#### 3.3.6 National Language Character Set Support

JDBC 4.0 introduces the `NCHAR`, `NVARCHAR`, `LONGNVARCHAR`, and `NCLOB` JDBC types to access the national character set types. These types are similar to the `CHAR`, `VARCHAR`, `LONGVARCHAR`, and `CLOB` types, except that the values are encoded using the national character set.

### 3.4 Support for JDBC 4.1 Standard

Oracle Database 12c Release 1 JDBC drivers provide support for JDBC 4.1 standard through JDK 7. This section describes the following important methods from JDBC 4.1 specification:

- `setClientInfo Method`

- `getObject Method`

#### 3.4.1 setClientInfo Method

For monitoring the consumption of the Database resources, you can use the `setClientInfo` method to identify the various application tasks using the Database at a given point of time. The `setClientInfo` method sets the value of the properties providing various application information. This method accepts keys of the form `<namespace>.<keyname>`. For example, you can use the `ACTION`, `MODULE`, and `CLIENTID` keys (that are found in the `V$SESSION` view and in many performance views and can be reported in trace files) with the `setClientInfo` method, as shown in the following code snippet:

    // "conn" is an instance of java.sql.Connection:
    conn.setClientInfo("OCSID.CLIENTID", "Alice_HR_Payroll");
    conn.setClientInfo("OCSID.MODULE", "APP_HR_PAYROLL");
    conn.setClientInfo("OCSID.ACTION", "PAYROLL_REPORT");

The `setClientInfo` method checks the Java permission `oracle.jdbc.clientInfo` and if the security check fails, then it throws a `SecurityException`. It supports permission name patterns of the form `<namespace>.*`. The `setClientInfo` method either sets or clears all pairs, so it requires that the permission name must be set to an asterisk (`*`).

The JDBC driver supports any `<namespace>.<keyname>` combination. The `setClientInfo` method supports the `OCSID` namespace among other namespaces. But, there are differences between using the `OCSID` namespace and any other namespace. With the `OCSID` namespace, the `setClientInfo` method supports only the following keys:

- `ACTION`

- `CLIENTID`

- `ECID`

- `MODULE`

- `SEQUENCE_NUMBER`

- `DBOP`

Also, the information associated with any other namespace is communicated through the network using a single protocol, while information associated with the OCSID namespace is communicated using a different protocol. The protocol used for the OCSID namespace is also used by the OCI C Library and the 10g JDBC thin driver and the later thin drivers to send end-to-end metrics values.

**Note:**

- The `setClientInfo` method is backward compatible with the `setEndToEndMetrics` and the `setClientIdentifier` methods, and can use DMS to set client tags.

- The `setEndToEndMetrics` method was deprecated in Oracle Database 12c Release 1 (12.1).

##### About Monitoring Database Operations

Many Java applications do not have a database connection, but they need to track database activities on behalf of their functionalities. For such applications, Oracle Database 12c Release 1 (12.1) introduced the `DBOP` tag that can be associated with a thread in the application when the application does not have explicit access to a database. The DBOP tag is associated with a thread through the invocation of DMS APIs, without requiring an active connection to the database. When the thread sends the next database call, then DMS propagates these tags through the connection along with the database call, without requiring an extra round trip. In this way, applications can associate their activity with database operations while factorizing the code in the Application layer. The `DBOP` tag composes of the following:

- Database operation name

- The execution ID

- Operation attributes

The `setClientInfo` method supports the `DBOP` tag. The `setClientInfo` method sets the value of the tag to monitor the database operations. When the JDBC application connects to the database and a database round-trip is made, the database activities can be tracked. For example, you can set the value of the `DBOP` tag to `foo` in the following way:

    ...
    Connection conn = DriverManager.getConnection(myUrl, myUsername, myPassword);
    conn.setClientInfo("E2E_CONTEXT.DBOP", "foo");
    Statement stmt = conn.createStatement();
    stmt.execute("select 1 from dual");  // DBOP tag is set after this
    ...

#### 3.4.2 getObject Method

The `getObject` method retrieves an object, based on the parameters passed. Oracle Database 12c Release 2 (12.2.0.1) supports the following two `getObject` methods:

##### Method 1

    <T> T getObject(int parameterIndex,
                    java.lang.Class<T> type)
                throws SQLException

##### Method 2

    <T> T getObject(java.lang.String parameterName,
                    java.lang.Class<T> type)
                throws SQLException

These methods support the conversions listed in the JDBC specification and also the additional conversions listed in [Table A-1](JDBC-reference-information.md). The Oracle Database 12c Release 2 (12.2.0.1) drivers also support conversions to some additional classes, which implement one or more static `valueOf` methods, if any of the following criteria is met:

- No other conversion is specified in JDBC specification or [Table A-1](JDBC-reference-information.md)

- The `type` argument defines one or more public static single argument methods named `valueOf`

- One or more of the `valueOf` methods take an argument that is a value of a type supported because of JDBC specification or [Table A-1](JDBC-reference-information.md)

This release of JDBC drivers convert the value to a type specified in the JDBC specification, or in [Table A-1](JDBC-reference-information.md) and then call the corresponding `valueOf` method with the converted value as the argument. If there is more than one appropriate `valueOf` method, then the JDBC driver chooses one `valueOf` method in an unspecified way.

##### Example

    ResultSet rs = . . . ;
    Character c = rs.getObject(1, java.lang.Character.class);

The Character class defines the following `valueOf` method:

    public static Character valueOf(char c);

[Table A-1](JDBC-reference-information.md) specifies that `NUMBER` can be converted to `char`. So, if the first column of the `ResultSet` is a `NUMBER`, then the `getObject` method converts that `NUMBER` value to a `char` and passes the `char` value to the `valueOf(char)` method and returns the resulting `Character` object.

### 3.5 Support for JDBC 4.2 Standard

Oracle Database 12c Release 2 (12.2.0.1) JDBC drivers provide support for JDBC 4.2 standard through JDK 8. This section describes some of the important methods added in this release.

#### The %Large% Methods

This release of Oracle JDBC drivers support the following methods introduced in JDBC 4.2 standard, which deal with `long` values:

- `executeLargeBatch()`

- `executeLargeUpdate(String sql)`

- `executeLargeUpdate(String sql, int autoGeneratedKeys)`

- `executeLargeUpdate(String sql, int[] columnIndexes)`

- `executeLargeUpdate(String sql, String[] columnNames)`

- `getLargeMaxRows()`

- `getLargeUpdateCount()`

- `setLargeMaxRows(long max)`

These new methods are available as part of the `java.sql.Statement` interface. The `%Large%` methods are identical to the corresponding non-large methods, except that they work with `long` values instead of `int` values. For example, the `executeUpdate` method returns the number of rows updated as an `int` value, whereas, the `executeLargeUpdate` method returns the number of rows updated as a `long` value. If the number of rows is greater than the value of `Integer.MAX_VALUE`, then your application must use the `executeLargeUpdate` method.

The following code snippet shows how to use the `executeLargeUpdate(String sql)` method:

    ...
    Statement stmt = conn.createStatement();
    stmt.executeQuery("create table BloggersData (FIRST_NAME varchar(100), ID int)");
    long updateCount = stmt.executeLargeUpdate("insert into BloggersData (FIRST_NAME,ID) values('John',1)");
    ...

#### The SQLType Methods

This release of Oracle JDBC drivers support the following methods introduced in JDBC 4.2 standard, which take `SQLType` parameters:

- `setObject`

  The `setObject` method sets the value of the designated parameter for the specified object. This method is similar to the `setObject(int parameterIndex, Object x, SQLType targetSqlType, int scaleOrLength)` method, except that it assumes a scale of zero. The default implementation of this method throws `SQLFeatureNotSupportedException`.

      void setObject(int parameterIndex, java.lang.Object x, SQLType targetSqlType) throws SQLException


  Where,

  `parameterIndex` is the index of the designated parameter, where the first parameter is 1, the second is 2, and so on

  `x` is the object containing the input parameter value

  `targetSqlType` is the SQL type to be sent to the database

- `updateObject`

  The `updateObject` method takes the column index as a parameter and updates the designated column with an Object value.

- `registerOutParameter`

  The `registerOutParameter` method registers a specified parameter to be of JDBC type `SQLType`.

The following code snippet shows how to use the `setObject` method:

    ...
    int empId = 100;
    connection.prepareStatement("SELECT FIRST_NAME, LAST_NAME FROM EMPLOYEES WHERE EMPNO = ?");
    preparedStatement.setObject(1, Integer.valueOf(empId), OracleType.NUMBER);
    ...

**Related Topics**

- <https://docs.oracle.com/javase/8/docs/technotes/guides/jdbc/jdbc_42.html>
