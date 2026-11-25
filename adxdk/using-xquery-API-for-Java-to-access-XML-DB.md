An explanation is given of how to use the XQuery API for Java (XQJ) to access Oracle XML DB.

### 16.1 Introduction to Oracle XML DB Support for XQJ

XQuery API for Java (XQJ), also known as JSR-225, provides an industry-standard way for Java programs to access Extensible Markup Language (XML) data using XQuery. It lets you evaluate XQuery expressions against XML data sources and process the results as XML data.

Oracle provides two XQuery engines for evaluating XQuery expressions: one in Oracle XML DB, for use with XML data in the database, and one in Oracle XML Developer's Kit (XDK), for use with XML data outside the database. (See [Using the XQuery Processor for Java](using-xquery-processor-for-Java.md) for information about the XQuery engine for XDK).

Oracle provides two different XQJ implementations for accessing these two XQuery engines. Both implementations are part of XDK, enabling you to use XDK to access XML data with a standard XQJ API whether that data resides in the database or elsewhere.

The queries executed by XQJ are written in standard World Wide Web Consortium (W3C) XQuery 1.0 language, as supported by Oracle XML DB. A typical use case for this feature is to access XML data stored in remote databases (in Oracle XML DB) from a local Java program.

General information about XQuery and XQJ is documented outside of this document.

**See Also:**

- [Oracle XML DB Developer’s Guide](../adxdb/intro-to-XML-DB.md) for more information about Oracle XML DB, including details about XQuery capabilities and support in Oracle XML DB

- `XQuery Packages` in [Oracle Database XML Java API Reference](../jaxml/index.md) for the related API documentation

- [JSR-000225 XQuery API for Java](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=jcp_org_jsr225), which is very concrete and has understandable examples

#### 16.1.1 Prerequisites for Using XQJ to Access Oracle XML DB

You need Java Runtime Environment 1.6 to use XQJ with Oracle XML DB. You also need certain Java Archive (JAR) files to be either in your `CLASSPATH` environment variable or passed using command-line option `classpath`.

The JAR files are as follows:

- The required JAR files listed in [Introduction to the XQuery Processor for Java](using-xquery-processor-for-Java.md)

- `jdbc/lib/ojdbc6.jar`

- `rdbms/jlib/xdb6.jar`

The directory paths for these JAR files are relative to the `ORACLE_HOME` directory of your database installation.

### 16.2 Examples: Using XQJ to Query Oracle XML DB

Examples here show how you can use XQJ to query and retrieve data in Oracle XML DB.

Example 16-1 shows how to use XQJ to query data from a table in Oracle XML DB. It uses the `WAREHOUSES` table in the Order Entry (OE) database sample schema. The OE sample schema contains XML documents with warehouse information in the `WAREHOUSES` table. The `WAREHOUSES` table contains an XMLType column `warehouse_spec` and other columns. (See the discussion about standard database schemas in [Oracle XML DB Developer’s Guide](../adxdb/preface.md) for more information about the data used in this example.)

Specifically, Example 16-1 shows how to perform these steps:

1.  Get an XQJ connection to Oracle XML DB.

    Every program using XQJ to connect to Oracle XML DB must first create an `OXQDDataSource` object. Then, `OXQDDataSource` must be initialized with the required property values before getting an XQJ connection to the Oracle XML DB instance.

2.  Prepare an XQuery expression.

3.  Submit the XQuery expression for evaluation.

4.  Print each item in the resulting XQuery sequence.

In Example 16-1, the XQuery expression accesses the `WAREHOUSES` table through the use of the Universal Resource Identifier (URI) scheme `oradb`. (See the discussion about the URI scheme `oradb` in [Oracle XML DB Developer’s Guide](../adxdb/xquery-and-XML-DB.md) for more information about using XQuery with XML DB to query table or view data.)

Example 16-1 also shows how to bind external variable values in XQJ. The query has an external variable `$x`, which is used to filter the returned rows from the `WAREHOUSES` table, by `WAREHOUSE_ID`.

Example 16-1 generates this output (reformatted for better readability):

    <Warehouse><Building>Owned</Building><Area>25000</Area><Docks>2</Docks>
     <DockType>Rearload</DockType><WaterAccess>Y</WaterAccess>
     <RailAccess>N</RailAccess><Parking>Street</Parking>
     <VClearance>10 ft</VClearance></Warehouse>

    <Warehouse><Building>Rented</Building><Area>50000</Area><Docks>1</Docks>
     <DockType>Sideload</DockType><WaterAccess>Y</WaterAccess>
     <RailAccess>N</RailAccess><Parking>Lot</Parking>
     <VClearance>12 ft</VClearance></Warehouse>

Example 16-2 shows how to use XQJ to retrieve data from the Oracle XML DB repository. This example assumes that two files, `depts.xml` and `emps.xml`, have been uploaded into the XML DB repository under the folder `/public`. For example, you can use FTP to upload the two files into the Oracle XML DB repository. (See the discussion about using the Oracle XML DB repository in [Oracle XML DB Developer’s Guide](../adxdb/index.md) for more information about storing data in and using the Oracle XML DB Repository.)

The content of `depts.xml` is:

    depts.xml:

    <?xml version="1.0"?>
         <depts>
           <dept deptno="10" dname="Administration"/>
           <dept deptno="20" dname="Marketing"/>
           <dept deptno="30" dname="Purchasing"/>
         </depts>

The content of `emps.xml` is:

    emps.xml:

    <?xml version="1.0"?>
       <emps>
        <emp empno="1" deptno="10" ename="John"  salary="21000"/>
           <emp empno="2" deptno="10" ename="Jack" salary="310000"/>
           <emp empno="3" deptno="20" ename="Jill" salary="100001"/>
         </emps>

You can use the `fn:doc` and `fn:collection` functions to query the data in the Oracle XML DB repository with XQuery. Example 16-2 shows how to use the `fn:doc` function within XQuery to access the repository. (See the discussion about querying XML data in the Oracle XML DB repository in [Oracle XML DB Developer’s Guide](../adxdb/query-and-update-XML.md) for more information about using these XQuery functions.)

Example 16-2 generates this output:

    <emp ename="Jack" dept="Administration"/>
    <emp ename="Jill" dept="Marketing"/>

Example 16-1 Using XQJ to Query an XML DB Table with XQuery

    import oracle.xml.xquery.xqjdb.OXQDDataSource;

    import javax.xml.xquery.XQItemType;
    import javax.xml.xquery.XQResultSequence;
    import javax.xml.xquery.XQConnection;
    import javax.xml.xquery.XQPreparedExpression;
    import javax.xml.namespace.QName;

    public class example1
    {
      public static void main(String argv[])
      {
        try
        {
          // Create a new OXQDDataSource for connecting to Oracle XML DB
          OXQDDataSource oxqDS = new OXQDDataSource();
          // Set appropriate connection information for the database instance.
          // Must use the thin driver
          oxqDS.setProperty("driver", "jdbc:oracle:thin");
          oxqDS.setProperty("dbusername", "oe");
          oxqDS.setProperty("dbpassword", "oe");
          // Machine hostname
          oxqDS.setProperty("dbserver", "myserver");
          // Database instance port number
          oxqDS.setProperty("dbport", "6479");
          // Database instance port number
          oxqDS.setProperty("serviceName", "mydbinstance");
          XQConnection conn = oxqDS.getConnection();
          XQItemType  itemTypeInt = conn.createAtomicType(XQItemType.XQBASETYPE_INT);
          XQPreparedExpression expr = conn.prepareExpression("declare variable $x as
            xs:int external; for $i in fn:collection('oradb:/OE/WAREHOUSES') where
              $i/ROW/WAREHOUSE_ID < $x return $i/ROW/WAREHOUSE_SPEC/Warehouse");
          expr.bindInt(new QName("x"), 3, itemTypeInt);
          XQResultSequence xqSeq = expr.executeQuery();
          while (xqSeq.next())
             System.out.println (xqSeq.getItemAsString(null));
         }
         catch (Exception e)
         {
          e.printStackTrace();
         }
      }
    }

Example 16-2 Using XQJ to Query the XML DB Repository with XQuery

    import oracle.xml.xquery.xqjdb.OXQDDataSource;

    import javax.xml.xquery.XQItemType;
    import javax.xml.xquery.XQResultSequence;
    import javax.xml.xquery.XQConnection;
    import javax.xml.xquery.XQPreparedExpression;
    import javax.xml.namespace.QName;

    public class example2
    {
      public static void main(String argv[])
      {
        try
        {
          // Create a new OXQDDataSource for connecting to Oracle XML DB
          OXQDDataSource oxqDS = new OXQDDataSource();
          // Set appropriate connection information for the database instance.
          // Must use the thin driver
          oxqDS.setProperty("driver", "jdbc:oracle:thin");
          oxqDS.setProperty("dbusername", "oe");
          oxqDS.setProperty("dbpassword", "oe");
          // Machine hostname
          oxqDS.setProperty("dbserver", "myserver");
          // Database instance port number
          oxqDS.setProperty("dbport", "6479");
          // Database instance port number
          oxqDS.setProperty("serviceName", "mydbinstance");
          XQConnection conn = oxqDS.getConnection();
          XQPreparedExpression expr = conn.prepareExpression("for $e in
            doc(\"/public/emps.xml\")/emps/emp let $d :=
            doc(\"/public/depts.xml\")//dept[@deptno = $e/@deptno]/@dname where
            $e/@salary > 100000 order by $e/@empno return
            <emp ename=\"{$e/@ename}\" dept=\"{$d}\"/>");
          XQResultSequence xqSeq = expr.executeQuery();
          while (xqSeq.next())
             System.out.println (xqSeq.getItemAsString(null));
         }
         catch (Exception e)
         {
          e.printStackTrace();
         }
      }
    }

### 16.3 XQJ Support for Oracle XML DB

The two Oracle XQJ implementations differ in some respects. Oracle XML DB support for XQJ is described.

[Using the XQuery Processor for Java](using-xquery-processor-for-Java.md) provides information about using XQJ to access the mid-tier XQuery engine.

Table 16-1 describes the OXQDDataSource properties to be used for connection to Oracle XML DB. To create an XQJ connection to Oracle XML DB, you must set the values for these properties. You must set either the `dbname` or the `serviceName` property value, and all the other OXQDDataSource property values listed in Table 16-1.

Table 16-1 OXQDDataSource Properties

| Property      | Value                                                   | Get Method       | Set Method       |
|:--------------|:--------------------------------------------------------|:-----------------|:-----------------|
| `driver`      | `jdbc:oracle:thin`                                      | `getDriver`      | `setDriver`      |
| `dbusername`  | Database schema (user) name                             | `getDBUserName`  | `setDBUserName`  |
| `dbpassword`  | Password for database schema                            | `getDBPassword`  | `setDBPassword`  |
| `dbserver`    | Host name for the database instance                     | `getDBServer`    | `setDBServer`    |
| `dbport`      | Port number of the database instance for XQJ connection | `getDBPort`      | `setDBPort`      |
| `dbname`      | Database instance name (service id)<sup>Foot 1</sup>    | `getDBName`      | `setDBName`      |
| `serviceName` | Service name<sup>Footref 1</sup>                        | `getServiceName` | `setServiceName` |

<sup>Footnote 1</sup>

You can identify the database using either the service id or the service name.

Table 16-2 describes the Oracle XML DB support for optional XQJ features.

**Note:**

Oracle XML DB support for some XQJ features differs from their support by the mid-tier XQuery engine. In particular, the Oracle XML DB XQJ implementation does not support the use of user-defined types.

Table 16-2 Oracle XML DB Support for Optional XQJ Features

| XQJ Feature                                                                                                                        | Oracle XML DB Support                                                                                                                                                                                         |
|:-----------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Class name of `XQDataSource` implementation                                                                                        | `oracle.xml.xquery.xqjdb.OXQDDataSource`                                                                                                                                                                      |
| JDBC connections                                                                                                                   | Not supported.                                                                                                                                                                                                |
| Properties defined on `OXQDDataSource` (connection information)                                                                    | See Table 16-1.                                                                                                                                                                                               |
| Commands                                                                                                                           | Not supported.                                                                                                                                                                                                |
| `XQPreparedExpression.cancel` (cancelling of query execution)                                                                      | Not supported.                                                                                                                                                                                                |
| Serialization                                                                                                                      | Only parameter `method` with value `xml` and parameter `encoding` with value `UTF-8` or `UTF-16`.                                                                                                             |
| Additional StAX and SAX events                                                                                                     | Not supported.                                                                                                                                                                                                |
| User-defined schema types                                                                                                          | Not supported.                                                                                                                                                                                                |
| Node identity, document order, and full-node context preservation when a node is bound to an external variable                     | Not supported.                                                                                                                                                                                                |
| Login timeout                                                                                                                      | Not supported.                                                                                                                                                                                                |
| Transactions                                                                                                                       | Not supported.                                                                                                                                                                                                |
| Behavior of `XQItemAccessor` method `getNodeUri()` when the input node is not a document node                                      | Return `NULL`.                                                                                                                                                                                                |
| Behavior of `XQItemType` method `getTypeName()` for anonymous types                                                                | Return `false`.                                                                                                                                                                                               |
| Behavior of `XQItemType` method `getSchemaURI()`                                                                                   | Return `NULL` or the schema URI provided during type creation. Currently, the Oracle XML DB XQJ implementation does not use the schema URI to get type information, and user-defined types are not supported. |
| Behavior of `XQDataFactory` methods `createItemFromDocument()` and `bindDocument()` if the input is not a well-formed XML document | Raise an exception.                                                                                                                                                                                           |
| Additional error codes returned from `XQQueryException`                                                                            | Not supported.                                                                                                                                                                                                |
| Interfaces `ConnectionPoolXQDataSource`, `PooledXQConnection`, `XQConnectionEvent`, `XQConnectionEventListener`                    | Not supported.                                                                                                                                                                                                |
| `XQDataSource.getConnection(`<br>`  java.sql.Connection)`                                                                          | Not supported. (JDBC connections are not supported.)                                                                                                                                                          |
| `XQDataSource.getConnection(`<br>`  java.lang.String,`<br>`  java.lang.String)`                                                    | Same as `getConnection()` with no arguments: the arguments are ignored.                                                                                                                                       |

**See Also:**

[Oracle XML DB Developer’s Guide](../adxdb/xquery-and-XML-DB.md) for information about using the XQuery language with Oracle XML DB

#### 16.3.1 Other Oracle XML DB XQJ Support Limitations

The limitations of Oracle XML DB support for XQJ are described. None of them apply to mid-tier XQuery engine support for XQJ.

Oracle XML DB support for XQJ is limited in these ways:

- All Oracle XML DB XQuery support limitations apply to Oracle XML DB support for XQJ as well.

- Only the XDK Document Object Model (DOM) is supported. Use of any other DOM can cause errors.

- Do not expect the Oracle XML DB XQJ implementation to be interoperable with another XQJ implementation, including the XDK Java implementation of XQJ. (See the XQJ standard (JSR-225) for the meaning of "interoperable".)

- `XQDataSource` methods `getLogWriter` and `setLogWriter` have no effect (they are ignored).

- `XQStaticContent` methods `getBoundarySpacePolicy`, `setBoundarySpacePolicy`, `getDefaultCollation`, and `setDefaultCollation` have no effect (they are ignored).

- The copy namespaces mode for `XQStaticContent` methods `setCopyNamespacesModPreserve` and `setCopyNamespacesModeInherit` has no effect (it is ignored). The values used are always `preserve` and `inherit`, respectively.

- Use of `XQDynamicContext` methods to bind `DocumentFragment` objects is not supported.

- Values of type `xs:duration` are not supported. Using an `XQDynamicContext` method to bind `xs:duration`, or accessing an `xs:duration` value, raises an error.

- The year of a `xs:date`, `xs:dateTime`, `xs:gYear`, and `xs:gYearMonth` value must be from -4712 to 9999, inclusive. Using a year outside this range can raise an error or produce unpredictable results.

### 16.4 XQJ Performance Considerations for Use with Oracle XML DB

To fetch a sequence of items from the database, use `XQResultSequence` method `next()` to retrieve a single item at a time; then use an `XQItemAccessor` method to fetch all data corresponding to that item.

This provides better performance than using these whole-sequence fetch methods, which each materialize the entire sequence before returning any data.

- `getSequenceAsStream()`

- `getSequenceAsString(java.util.Properties props)`

- `writeSequence(java.io.OutputStream os, java.util.Properties props)`

- `writeSequence(java.io.Writer ow, java.util.Properties props)`

- `writeSequenceToResult(javax.xml.transform.Result result)`

- `writeSequenceToSAX(org.xml.sax.ContentHandler saxhdlr)`

For example, if you invoke `getSequenceAsStream()`, all of the XQuery result sequence data is fetched from the database before the `XMLStreamReader` instance that is built from it is returned to your program.

Be aware also that items themselves are not streamable: the item accessor methods always materialize an entire item before outputting any part of it.

For inputting, all bind methods defined on `XQDynamicContext` fully materialize the input data before passing it to the database.

For example, when you invoke `bindDocument(javax.xml.namespace.QName varName, javax.xml.stream.XMLStreamReader value, XQItemType type)`, all the data that is referenced by the input `XMLStreamReader` instance is processed before the external XQuery variable is bound to it.
