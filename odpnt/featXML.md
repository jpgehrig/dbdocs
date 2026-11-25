ODP.NET allows the extraction of data from relational and object-relational tables and views as XML documents. The use of XML documents for insert, update, and delete operations to the database is also allowed. Oracle Database supports XML natively in the database, through Oracle XML DB, a distinct group of technologies related to high-performance XML storage and retrieval. Oracle XML DB is an evolution of the database that encompasses both SQL and XML data models in a highly interoperable manner, providing native XML support.

ODP.NET, Managed Driver follows XPath 1.0 specification and hence it does not support default XML namespaces. XML namespaces must be explicitly added to search or update nodes. This behavior differs from ODP.NET, Unmanaged Driver.

For samples related to ODP.NET XML support in ODAC installations done using Oracle Universal Installer, see the following directory:

    ORACLE_BASE\ORACLE_HOME\ODACsamples

This section includes these topics:

- Supported XML Features

- OracleXmlType and Connection Dependency

- Updating XMLType Data in the Database

- Updating XML Data in OracleXmlType

- Characters with Special Meaning in XML

- Retrieving Query Result Set as XML

- Data Manipulation Using XML

### Supported XML Features

XML support in ODP.NET provides the ability to do the following:

- Store XML data natively in the database as the Oracle database native type, `XMLType`.

- Access relational and object-relational data as XML data from an Oracle Database instance into the Microsoft .NET environment, and process the XML using the Microsoft .NET Framework.

- Save changes to the database using XML data.

- Execute XQuery statements.

For the .NET application developer, these features include the following:

- Enhancements to the `OracleCommand`, `OracleConnection`, and `OracleDataReader` classes.

- The following XML-specific classes:

  - `OracleXmlType`

    `OracleXmlType` objects are used to retrieve Oracle native `XMLType` data.

  - `OracleXmlStream`

    `OracleXmlStream` objects are used to retrieve XML data from `OracleXmlType` objects as a read-only .NET `Stream` object.

  - `OracleXmlQueryProperties`

    `OracleXmlQueryProperties` objects represent the XML properties used by the `OracleCommand` class when the `XmlCommandType` property is `Query`.

  - `OracleXmlSaveProperties`

    `OracleXmlSaveProperties` objects represent the XML properties used by the `OracleCommand` class when the `XmlCommandType` property is `Insert`, `Update`, or `Delete`.

  **See Also:**

  - "XQuery Support"

  - "[OracleCommand Class](OracleCommandClass.md)"

  - "[OracleXmlType Class](OracleXmlTypeClass.md)"

  - "[OracleXmlStream Class](OracleXmlStreamClass.md)"

  - "[OracleXmlQueryProperties Class](OracleXmlQueryPropertiesClass.md)"

  - "[OracleXmlSaveProperties Class](OracleXmlSavePropertiesClass.md)"

  - [Oracle XML DB Developer’s Guide](../adxdb/XML-DB-and-ODP-for-dot-NET.md)

### XQuery Support

ODP.NET supports the XQuery language through a native implementation of SQL/XML functions, `XMLQuery` and `XMLTable`. When executing XQuery statements, Oracle XML DB generally evaluates XQuery expressions by compiling them into the same underlying structures as relational queries. Queries are optimized, leveraging both relational-database and XQuery-specific optimization technologies, so that Oracle XML DB serves as a native XQuery engine.The treatment of all XQuery expressions, whether natively compiled or evaluated functionally, is transparent: programmers do not need to change their code to take advantage of XQuery optimizations.

**See Also:**

[Oracle XML DB Developer's Guide](../adxdb/xquery-and-XML-DB.md) to learn more about Oracle's XQuery support

### OracleXmlType and Connection Dependency

The read-only `Connection` property of the `OracleXmlType` class holds a reference to the `OracleConnection` object used to instantiate the `OracleXmlType` class.

How the `OracleXmlType` object obtains a reference to an `OracleConnection` object depends on how the `OracleXmlType` class is instantiated:

- Instantiated from an `OracleDataReader` class using the `GetOracleXmlType`, `GetOracleValue`, or `GetOracleValues` method:

  The `Connection` property is set with a reference to the same `OracleConnection` object used by the `OracleDataReader` object.

- Instantiated by invoking an `OracleXmlType` constructor with one of the parameters of type `OracleConnection`:

  The `Connection` property is set with a reference to the same `OracleConnection` object provided in the constructor.

- Instantiated by invoking an `OracleXmlType(OracleClob)` constructor:

  The `Connection` property is set with a reference to the `OracleConnection` object used by the `OracleClob` object.

An `OracleXmlType` object that is associated with one connection cannot be used with a different connection. For example, if an `OracleXmlType` object is obtained using `OracleConnection` `A`, that `OracleXmlType` object cannot be used as an input parameter of a command that uses `OracleConnection` `B`. By checking the `Connection` property of the `OracleXmlType` objects, the application can ensure that `OracleXmlType` objects are used only within the context of the `OracleConnection` referenced by its connection property. Otherwise, ODP.NET raises an exception.

### Updating XMLType Data in the Database

Updating `XMLType` columns does not require a transaction. However, encapsulating the entire database update process within a transaction is highly recommended. This allows the updates to be rolled back if there are any errors.

`XMLType` columns in the database can be updated using Oracle Data Provider for .NET in a few ways:

- Updating with DataSet, OracleDataAdapter, and OracleCommandBuilder

- Updating with OracleCommand and OracleParameter

#### Updating with DataSet, OracleDataAdapter, and OracleCommandBuilder

If the `XMLType` column is fetched into the `DataSet`, the `XMLType` data is represented as a .NET `String`.

Modifying `XMLType` data in the `DataSet` does not require special treatment. `XMLType` data can be modified in the same way as any data that is stored in the `DataSet`. When a change is made and the `OracleDataAdapter.Update` method is invoked, the `OracleDataAdapter` object ensures that the `XMLType` data is handled properly. The `OracleDataAdapter` object uses any custom SQL `INSERT`, `UPDATE`, or `DELETE` statements that are provided. Otherwise, valid SQL statements are generated by the `OracleCommandBuilder` object as needed to [flush](glossary.md) the changes to the database.

#### Updating with OracleCommand and OracleParameter

The `OracleCommand` class provides a powerful way of updating `XMLType` data, especially with the use of an `OracleParameter` object. To update columns in a database table, the new value for the column can be passed as an input parameter of a command.

##### Input Binding

To update an `XMLType` column in the database, a SQL statement can be executed using static values. In addition, input parameters can be bound to SQL statements, anonymous PL/SQL blocks, or stored procedures to update `XMLType` columns. The parameter value can be set as .NET Framework Types, ODP.NET Types, or `OracleXmlType` objects.

While `XMLType` columns can be updated using an `OracleXmlType` object, having an instance of an `OracleXmlType` class does not guarantee that the `XMLType` column in the database can be updated.

##### Setting XMLType Column to NULL Value

Applications can set an `XMLType` column in the database to a `NULL` value, with or without input binding, as follows:

- Setting `NULL` values in an `XMLType` column with input binding

  To set the `XMLType` column to `NULL`, the application can bind an input parameter whose value is `DBNull`.`Value`. This indicates to the `OracleCommand` object that a `NULL` value is to be inserted.

  Passing in a null `OracleXmlType` object as an input parameter does not insert a `NULL` value into the `XMLType` column. In this case, the `OracleCommand` object raises an exception.

- Setting `NULL` Values in an `XMLType` Column without input binding

  The following example demonstrates setting `NULL` values in an `XMLType` column without input binding:

      // Create a table with an XMLType column in the database
      CREATE TABLE XML_TABLE(NUM_COL number, XMLTYPE_COL xmltype);

  An application can set a `NULL` value in the `XMLType` column by explicitly inserting a `NULL` value or by not inserting anything into that column as in the following examples:

      insert into xml_table(xmltype_col) values(NULL);

      update xml_table t set t.xmltype_col=NULL;

##### Setting XMLType Column to Empty XML Data

The `XMLType` column can be initialized with empty XML data, using a SQL statement:

    // Create a table with an XMLType column in the database
    CREATE TABLE XML_TABLE(NUM_COL number, XMLTYPE_COL xmltype);

    INSERT INTO XML_TABLE (NUM_COL, XMLTYPE_COL) VALUES (4,
          XMLType.createxml('<DOC/>'));

### Updating XML Data in OracleXmlType

The following are ways that XML data can be updated in an `OracleXmlType` object.

- The XML data can be updated by passing an XPATH expression and the new value to the `Update` method on the `OracleXmlType` object.

- The XML data can be retrieved on the client side as the .NET Framework `XmlDocument` object using the `GetXmlDocument` method on the `OracleXmlType` object. This XML data can then be manipulated using suitable .NET Framework classes. A new `OracleXmlType` can be created with the updated XML data from the .NET Framework classes. This new `OracleXmlType` is bound as an input parameter to an update or insert statement.

### Characters with Special Meaning in XML

The following characters in Table 3-20 have special meaning in XML. For more information, refer to the XML 1.0 specifications

Table 3-20 Characters with Special Meaning in XML

| Character | Meaning in XML                      | Entity Encoding |
|:----------|:------------------------------------|:----------------|
| \<        | Begins an XML tag                   | &lt;            |
| \>        | Ends an XML tag                     | &gt;            |
| "         | Quotation mark                      | &quot;          |
| '         | Apostrophe or single quotation mark | &apos;          |
| &         | Ampersand                           | &amp;           |

When these characters appear as data in an XML element, they are replaced with their equivalent entity encoding.

Also certain characters are not valid in XML element names. When SQL identifiers (such as column names) are mapped to XML element names, these characters are converted to a sequence of hexadecimal digits, derived from the Unicode encoding of the character, bracketed by an introductory underscore, a lowercase `x` and a trailing underscore. A blank space is not a valid character in an XML element name. If a SQL identifier contains a space character, then in the corresponding XML element name, the space character is replaced by `_x0020_`, which is based on Unicode encoding of the space character.

### Retrieving Query Result Set as XML

This section discusses retrieving the result set from a SQL query as XML data.

#### Handling Date and Time Format

The generated XML `DATE` and `TIMESTAMP` formats are based on the standard XML Schema formats.

**See Also:**

[`http://www.w3.org/TR/2004/REC-xmlschema-2-20041028/datatypes.html#isoformats`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/odpnt&id=w3_org_xschema_isoformats) for more information on the XML Schema specification.

#### Characters with Special Meaning in Column Data

If the data in any of the select list columns in the query contains any characters with special meaning in XML (see Table 3-20), these characters are replaced with their corresponding entity encoding in the result XML document.

The following examples demonstrate how ODP.NET handles the angle bracket characters in the column data:

    /* Database Setup
    connect scott/tiger@oracle
    drop table specialchars;
    create table specialchars ("id" number, name varchar2(255));
    insert into specialchars values (1, '<Jones>');
    commit;
    */

    // C#

    using System;
    using System.Data;
    using System.Xml;
    using Oracle.DataAccess.Client;

    class QueryResultAsXMLSample
    {
      static void Main()
      {
        OracleConnection con = new OracleConnection();

        con.ConnectionString = "User Id=scott;Password=tiger;Data Source=oracle;";
        con.Open();

        // Create the command
        OracleCommand cmd = new OracleCommand("", con);

        // Set the XML command type to query.
        cmd.XmlCommandType = OracleXmlCommandType.Query;

        // Set the SQL query
        cmd.CommandText = "select * from specialchars";

        // Set command properties that affect XML query behavior.
        cmd.BindByName = true;

        // Set the XML query properties
        cmd.XmlQueryProperties.MaxRows = -1;

        // Get the XML document as an XmlReader.
        XmlReader xmlReader = cmd.ExecuteXmlReader();
        XmlDocument xmlDocument = new XmlDocument();

        xmlDocument.PreserveWhitespace = true;
        xmlDocument.Load(xmlReader);
        Console.WriteLine(xmlDocument.OuterXml);

        // Close and Dispose OracleConnection object
        con.Close();
        con.Dispose();
      }
    }

The following XML document is generated for that table: The XML entity encoding that represents the angle brackets appears in bold.

    <?xml version = '1.0'?>
    <ROWSET>
       <ROW>
          <id>1</id >
          <NAME>&lt;Jones&gt;</NAME>
       </ROW>
    </ROWSET>

#### Characters in Table or View Name

If a table or view name has any non-alphanumeric characters other than an underscore (\_), the table or view name must be enclosed in quotation marks.

For example, to select all entries from a table with the name `test'ing`, the `CommandText` property of the `OracleCommand` object must be set to the following string:

    "select * from \"test'ing\"";

#### Case-Sensitivity in Column Name to XML Element Name Mapping

The mapping of SQL identifiers (column names) to XML element names is case- sensitive, and the element names are in exactly the same case as the column names of the table or view.

However, the root tag and row tag names are case-insensitive. The following example demonstrates case-sensitivity in this situation:

    //Create the following table
    create table casesensitive_table ("Id" number, NAME varchar2(255));

    //insert name and id
    insert into casesensitive_table values(1, 'Smith');


The following XML document is generated:

    <?xml version = '1.0'?>
      <ROWSET>
        <ROW>
          <Id>1</Id>
          <NAME>Smith</NAME>
        </ROW>
      </ROWSET>

Note that the element name for the `Id` column matches the case of the column name.

#### Column Name to XML Element Name Mapping

For each row generated by the SQL query, the SQL identifier (column name) maps to an XML element in the generated XML document, as shown in the following example:

    // Create the following table
    create table emp_table (EMPLOYEE_ID NUMBER(4), LAST_NAME varchar2(25));
    // Insert some data
    insert into emp_table values(205, 'Higgins');

The SQL query, `SELECT` `*` `FROM` `EMP_TABLE`, generates the following XML document:

    <?XML version="1.0"?>
      <ROWSET>
        <ROW>
          <EMPLOYEE_ID>205</EMPLOYEE_ID>
          <LAST_NAME>Higgins</LAST_NAME>
        </ROW>
      </ROWSET>

The `EMPLOYEE_ID` and `LAST_NAME` database columns of the `employees` table map to the `EMPLOYEE_ID` and `LAST_NAME` elements of the generated XML document.

This section demonstrates how Oracle database handles the mapping of SQL identifiers to XML element names, when retrieving query results as XML from the database. The demonstration uses the `specialchars` table involving the `some` `id` column.

    // Create the specialchars table
    create table specialchars ("some id" number, name varchar2(255));

Note that the `specialchars` table has a column named `some` `id` that contains a blank space character. The space character is not allowed in an XML element name.

When retrieving the query results as XML, the SQL identifiers in the query select list can contain characters that are not valid in XML element names. When these SQL identifiers (such as column names) are mapped to XML element names, each of these characters is converted to a sequence of hexadecimal digits, derived from the Unicode encoding of the characters, bracketed by an introductory underscore, a lowercase x, and a trailing underscore.

Thus, the SQL query in the following example can be used to get a result as an XML document from the `specialchars` table:

    select "some id", name from specialchars;

**See Also:**

"Characters with Special Meaning in XML"

##### Improving Default Mapping

You can improve the default mapping of SQL identifiers to XML element names by using the following techniques:

- Modify the source. Create an object-relational view over the source schema, and make that view the new source.

- Use cursor subqueries and cast-multiset constructs in the SQL query.

- Create an alias for the column or attribute names in the SQL query. Prefix the aliases with an at sign (@) to map them to XML attributes instead of XML elements.

- Modify the XML document. Use [Extensible Stylesheet Language Transformation (XSLT)](glossary.md) to transform the XML document. Specify the XSL document and parameters. The transformation is done automatically after the XML document is generated from the relational data. Note that this may have an impact on performance.

- Specify the name of the root tag and row tag used in the XML document.

#### Object-Relational Data

ODP.NET can generate an XML document for data stored in object-relational columns, tables, and views, as shown in the following example:

    // Create the following tables and types
    CREATE TYPE "EmployeeType" AS OBJECT (EMPNO NUMBER, ENAME VARCHAR2(20));
    /
    CREATE TYPE EmployeeListType AS TABLE OF "EmployeeType";
    /
    CREATE TABLE mydept (DEPTNO NUMBER, DEPTNAME VARCHAR2(20),
                  EMPLIST EmployeeListType)
                  NESTED TABLE EMPLIST STORE AS EMPLIST_TABLE;
    INSERT INTO mydept VALUES (1, 'depta',
                  EmployeeListType("EmployeeType"(1, 'empa')));

The following XML document is generated for the table:

    <?xml version = "1.0"?>
    <ROWSET>
       <ROW>
          <DEPTNO>1</DEPTNO>
          <DEPTNAME>depta</DEPTNAME>
          <EMPLIST>
             <EmployeeType>
                <EMPNO>1</EMPNO>
                <ENAME>empa</ENAME>
             </EmployeeType>
          </EMPLIST>
       </ROW>
    </ROWSET>

ODP.NET encloses each item in a collection element, with the database type name of the element in the collection. The `mydept` table has a collection in the `EMPLIST` database column and each item in the collection is of type `EmployeeType`. Therefore, in the XML document, each item in the collection is enclosed in the type name `EmployeeType`, which appears in bold in the example.

#### NULL Values

If any database row has a column with a `NULL` value, then that column does not appear for that row in the generated XML document.

### Data Manipulation Using XML

This section discusses making changes to the database data using XML.

#### Handling Date and Time Format

The generated XML `DATE` and `TIMESTAMP` formats are based on the standard XML Schema formats.

**See Also:**

[`http://www.w3.org/TR/2004/REC-xmlschema-2-20041028/datatypes.html#isoformats`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/odpnt&id=w3_org_xschema_isoformats) for more information on the XML Schema specification.

#### Saving Changes Using XML

Changes can be saved to database tables and views using XML data. However, insert, update, and delete operations cannot be combined in a single XML document. ODP.NET cannot accept a single XML document and determine which are insert, update, or delete changes.

The insert change must be in an XML document containing only rows to be inserted, the update changes only with rows to be updated, and the delete changes only with rows to be deleted.

For example, using the `employees` table that comes with the HR sample schema, you can specify the following query:

    select employee_id, last_name from employees where employee_id = 205;

The following XML document is generated:

    <?xml version = '1.0'?>
    <ROWSET>
       <ROW>
          <EMPLOYEE_ID>205</EMPLOYEE_ID>
          <LAST_NAME>Higgins</LAST_NAME>
       </ROW>
    </ROWSET>

To change the name of employee `205` from `Higgins` to `Smith`, specify the `employees` table and the XML data containing the changes as follows:

    <?xml version = '1.0'?>
    <ROWSET>
       <ROW>
          <EMPLOYEE_ID>205</EMPLOYEE_ID>
          <LAST_NAME>Smith</LAST_NAME>
       </ROW>
    </ROWSET>

#### Characters with Special Meaning in Column Data

If the data in any of the elements in the XML document contains characters that have a special meaning in XML (see Table 3-20), these characters must be replaced with appropriate entity encoding, or be preceded by an escape character in the XML document, so that the data is stored correctly in the database table column. Otherwise, ODP.NET throws an exception.

The following example demonstrates how ODP.NET handles the angle bracket special characters in the column data, using entity encoding:

    // Create the following table
    create table specialchars ("id" number, name varchar2(255));

The following XML document can be used to insert values `(1,` `'<Jones>')` into the `specialchars` table. The XML entity encoding that represents the angle brackets appears in bold.

    <?xml version = '1.0'?>
     <ROWSET>
      <ROW>
       <id>1</id >
       <NAME>&lt;Jones&gt;</NAME>
      </ROW>
     </ROWSET>

#### Characters with Special Meaning in Table or View Name

If a table or view name has any non-alphanumeric characters other than an underscore (\_), the table or view name must be enclosed in quotation marks.

For example, to save changes to a table with the name `test'ing`, the `OracleCommand.XmlSaveProperties.TableName` property must be set to `"\"test'ing\""`.

#### Case-Sensitivity in XML Element Name to Column Name Mapping

For each XML element that represents a row of data in the XML document, the child XML elements map to database column names. The mapping of the child element name to the column name is always case-sensitive, but the root tag and row tag names are case-insensitive. The following example demonstrates this case-sensitivity:

    //Create the following table
    create table casesensitive_table ("Id" number, NAME varchar2(255));

The following XML document can be used to insert values (`1`, `Smith`) into the `casesensitive_table`:

    <?xml version = '1.0'?>
      <ROWSET>
        <ROW>
          <Id>1</Id>
          <NAME>Smith</NAME>
        </ROW>
      </ROWSET>

Note that the element name for the `Id` column matches the case of the column name.

#### XML Element Name to Column Name Mapping

This section describes how Oracle database handles the mapping of XML element names to column names when using XML for data manipulation in the database. The following `specialchars` table involving the `some` `id` column demonstrates this handling.

    // Create the specialchars table
    create table specialchars ("some id" number, name varchar2(255));

Note that the `specialchars` table has a column named `some` `id` that contains a blank space character. The space character is not allowed in an XML element name.

#### Saving Changes to a Table Using an XML Document

When an XML document is used to save changes to a table or view, the `OracleCommand.XmlSaveProperties.UpdateColumnsList` property is used to specify the list of columns to update or insert.

When an XML document is used to save changes to a column in a table or view, and the corresponding column name contains any of the characters that are not valid in an XML element name, the escaped column name must be specified in the `UpdateColumnsList` property as in the following example.

The following XML document can be used to insert values (`2`, `<Jones>`) into the `specialchars` table:

    <?xml version = '1.0'?>
      <ROWSET>
        <ROW>
          <some_x0020_id>2</some_x0020_id>
          <NAME>&lt;Jones&gt;</NAME>
        </ROW>
      </ROWSET>

The following example specifies the list of columns to update or insert:

    /* Database Setup
    connect scott/tiger@oracle
    drop table specialchars;
    create table specialchars ("some id" number, name varchar2(255));
    insert into specialchars values (1, '<Jones>');
    commit;
    */

    // C#

    using System;
    using System.Data;
    using System.Xml;
    using Oracle.DataAccess.Client;

    class InsertUsingXmlDocSample
    {
      static void Main()
      {
        OracleConnection con = new OracleConnection();

        con.ConnectionString = "User Id=scott;Password=tiger;Data Source=oracle;";
        con.Open();
        Console.WriteLine("Connected Successfully");

        // Create the command
        OracleCommand cmd = new OracleCommand("", con);

        // Set the XML command type to query.
        cmd.XmlCommandType = OracleXmlCommandType.Insert;

        // Set the XML document
        cmd.CommandText = "<?xml version = '1.0'?>\n" + "<ROWSET>\n" + "<ROW>\n" +
          "<some_x0020_id>2</some_x0020_id>\n" + "<NAME>&lt;Jones&gt;</NAME>\n" +
          "</ROW>\n" + "</ROWSET>\n";
        cmd.XmlSaveProperties.Table = "specialchars";

        string[] ucols = new string[2];

        ucols[0] = "some_x0020_id";
        ucols[1] = "NAME";
        cmd.XmlSaveProperties.UpdateColumnsList = ucols;

        // Insert rows
        int rows = cmd.ExecuteNonQuery();

        Console.WriteLine("Number of rows inserted successfully : {0} ", rows);

        // Close and Dispose OracleConnection object
        con.Close();
        con.Dispose();
      }
    }

##### Improving Default Mapping

You can improve the default mapping by using the following techniques:

- Modify the target. Create an object-relational view over the target schema, and make the view the new target.

- Modify the XML document. Use XSLT to transform the XML document. Specify the XSL document and parameters. The transformation is done before the changes are saved. Note that this is may have an impact on performance.

- Specify the name of the row tag used in the XML document.

#### Object-Relational Data

Changes in an XML document can also be saved to object-relational data. Each item in a collection can be specified in one of the following ways in the XML document:

- By enclosing the database type name of the item as the XML element name.

- By enclosing the name of the database column holding the collection with `_ITEM` appended as the XML element name.

#### Multiple Tables

Oracle Database does not save changes to multiple relational tables that have been joined together. Oracle recommends that you create a view on those relational tables, and then update that view. If the view cannot be updated, triggers can be used instead.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/ALTER-USER.md) for the description and syntax of the `CREATE` `VIEW` statement

#### Commit Transactions

When the changes in an XML document are made, either all the changes are committed, or if an error occurs, all changes are rolled back.
