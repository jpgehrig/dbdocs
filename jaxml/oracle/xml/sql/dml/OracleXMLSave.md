Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Class**
- **Next Class**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**oracle.xml.sql.dml**

## **Class OracleXMLSave**

- **java.lang.Object**

- - **oracle.xml.sql.dml.OracleXMLSave**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class OracleXMLSave
      extends java.lang.Object

  **OracleXMLSave - This class supports canonical mapping from XML to object-relational tables and views. You must initially create a class by passing in the table name to which DML operations apply. You can subsequently use any of the insertion, update, and deletion methods of the `OracleXMLSave` class on the table. Many useful functions are provided to help identify key columns for UPDATE or DELETE, and to restrict the set of columns being updated. A typical sequence might look like this:**
  - **Create an instance of the class:**

        OracleXMLSave sav = new OracleXMLSave(conn, "emp");

  - **Insert data from an XML document:**

        sav.insertXML(xmlDoc);

  - **Update rows, driven by an XML document, and specifying key column:**

        String[] keyArray = new String[1];

        keyArray[0] = EMPNO";

        sav.setKeyColumnList(keyArray);

        sav.updateXML(xmlDoc);


  - **Delete rows, driven by an XML document:**

        sav.deleteXML(xmlDoc);

  - **Clean up:**

        sav.close();

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                |
    |---------------------------|----------------------------------------------------------------------|
    | `static java.lang.String` | `DATE_FORMAT`<br>The date format for use in `setDateFormat`.         |
    | `static int`              | `DEFAULT_BATCH_SIZE`<br>The default insert batch size is 17 records. |
    | `boolean`                 | `xDocIsEsc`                                                          |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                           |
    |-----------------------------------------------------------------------------------------------------------------------|
    | `OracleXMLSave``(java.sql.Connection conn, java.lang.String tableName)`<br>Constructor for the `OracleXMLSave` class. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                                                                                                                             |
    |-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                | `cleanLobList``()`<br>This function frees all temporary LOBs                                                                                                                                                       |
    | `void`                | `close``()`<br>Closes the `OracleXMLSave` object and deallocates all context associated with it.                                                                                                                   |
    | `java.net.URL`        | `createURL``(java.lang.String fileName)`<br>Returns the URL object for a specified file or URL.                                                                                                                    |
    | `int`                 | `deleteXML``(`[`Document`](../../../../org/w3c/dom/Document.md)` doc)`<br>Deletes the rows in the table based on the XML document By default, matches all XML element values with corresponding column names.      |
    | `int`                 | `deleteXML``(java.io.InputStream xmlStream)`<br>Deletes the rows in the table based on the XML document.                                                                                                           |
    | `int`                 | `deleteXML``(java.io.Reader xmlStream)`<br>Deletes the rows in the table based on the XML document.                                                                                                                |
    | `int`                 | `deleteXML``(java.lang.String xmlDoc)`<br>Deletes the rows in the table based on the XML document.                                                                                                                 |
    | `int`                 | `deleteXML``(java.net.URL url)`<br>Deletes rows from a table based on element values of the input XML document.                                                                                                    |
    | `static java.net.URL` | `getURL``(java.lang.String target)`<br>Given a file name or a URL it return a URL object.                                                                                                                          |
    | `int`                 | `insertXML``(`[`Document`](../../../../org/w3c/dom/Document.md)` doc)`                                                                                                                                             |
    | `int`                 | `insertXML``(java.io.InputStream xmlStream)`                                                                                                                                                                       |
    | `int`                 | `insertXML``(java.io.Reader xmlStream)`                                                                                                                                                                            |
    | `int`                 | `insertXML``(java.lang.String xmlDoc)`                                                                                                                                                                             |
    | `int`                 | `insertXML``(java.net.URL url)`<br>Inserts an XML document from a specified URL into a table, By default, matches element names to column names, and sets columns with missing elements in input to `null</null>.` |
    | `void`                | `removeXSLTParam``(java.lang.String name)`<br>Removes the value of a top-level stylesheet parameter.                                                                                                               |
    | `void`                | `setBatchSize``(int size)`<br>Changes the batch size used during DML operations.                                                                                                                                   |
    | `void`                | `setCommitBatch``(int size)`<br>Sets the commit batch size, or the number of records inserted before a commit.                                                                                                     |
    | `void`                | `setDateFormat``(java.lang.String mask)`<br>Specifies the format of dates used in the XML document.                                                                                                                |
    | `void`                | `setIgnoreCase``(boolean ignore)`<br>Sets the comparison mode.                                                                                                                                                     |
    | `void`                | `setKeyColumnList``(java.lang.String[] keyColNames)`<br>Sets the list of columns used to identify table rows against XML input document elements prior to `UPDATE` and `DELETE` operations.                        |
    | `void`                | `setPreserveWhitespace``(boolean flag)`<br>Specifies whether to preserve whitespace..                                                                                                                              |
    | `void`                | `setRowTag``(java.lang.String rowTag)`<br>Names the tag for the row enclosing XML element.                                                                                                                         |
    | `void`                | `setSQLToXMLNameEscaping``(boolean flag)`<br>Determines whether to turn on XML tag escaping for SQL object names, to ensure conversion to valid XML identifiers.                                                   |
    | `void`                | `setUpdateColumnList``(java.lang.String[] updColNames)`<br>Sets and limits the list of columns for `INSERT` and `UPDATE` operations.                                                                               |
    | `void`                | `setXSLT``(java.io.Reader stylesheet, java.lang.String ref)`<br>Registers an XSL transformation that should be applied to generated XML.                                                                           |
    | `void`                | `setXSLT``(java.lang.String stylesheet, java.lang.String ref)`<br>Registers an XSL transformation that should be applied to generated XML.                                                                         |
    | `void`                | `setXSLTParam``(java.lang.String name, java.lang.String value)`<br>Sets the value of the top-level stylesheet parameter.                                                                                           |
    | `int`                 | `updateXML``(`[`Document`](../../../../org/w3c/dom/Document.md)` doc)`<br>Updates the table given the XML document in a DOM tree form.                                                                             |
    | `int`                 | `updateXML``(java.io.InputStream xmlStream)`<br>Updates the table given the XML document in a stream form.                                                                                                         |
    | `int`                 | `updateXML``(java.io.Reader xmlStream)`<br>Updates the table given the XML document in a stream form.                                                                                                              |
    | `int`                 | `updateXML``(java.lang.String xmlDoc)`<br>Updates the table given the XML document in a string form.                                                                                                               |
    | `int`                 | `updateXML``(java.net.URL url)`<br>Updates the columns in a database table, based on the element values in the input XML document.                                                                                 |
    | `void`                | `useDBDates``(boolean flag)`<br>Tells XSU to assume dates in XML doc are in DB format.                                                                                                                             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### DEFAULT_BATCH_SIZE

          public static final int DEFAULT_BATCH_SIZE

      The default insert batch size is 17 records.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DATE_FORMAT

          public static final java.lang.String DATE_FORMAT

      The date format for use in `setDateFormat`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### xDocIsEsc

          public boolean xDocIsEsc

  <!-- -->

  - ### Constructor Detail

    - #### OracleXMLSave

          public OracleXMLSave(java.sql.Connection conn,
                               java.lang.String tableName)

      Constructor for the `OracleXMLSave` class.
      Parameters:
      `conn` - `Connection` object for accessing the database

      `tableName` - The name of the table that should be updated

  <!-- -->

  - ### Method Detail

    - #### setPreserveWhitespace

          public void setPreserveWhitespace(boolean flag)

      Specifies whether to preserve whitespace..
      Parameters:
      `flag` - `TRUE` to preserve whitespace

    <!-- -->

    - #### useDBDates

          public void useDBDates(boolean flag)

      Tells XSU to assume dates in XML doc are in DB format.
      Parameters:
      `flag` - use DB dates?

    <!-- -->

    - #### setXSLT

          public void setXSLT(java.lang.String stylesheet,
                              java.lang.String ref)

      Registers an XSL transformation that should be applied to generated XML. Replaces a previously registered stylesheet. To deregister the stylesheet, pass a `null` in the `stylesheet` parameter.
      Parameters:
      `stylesheet` - the stylesheet URI

      `ref` - URL for include, import and external entities

    <!-- -->

    - #### setXSLT

          public void setXSLT(java.io.Reader stylesheet,
                              java.lang.String ref)

      Registers an XSL transformation that should be applied to generated XML. Replaces a previously registered stylesheet. To deregister the stylesheet, pass a `null` in the `stylesheet` parameter.
      Parameters:
      `stylesheet` - the stylesheet

      `ref` - URL for include, import and external entities

    <!-- -->

    - #### setXSLTParam

          public void setXSLTParam(java.lang.String name,
                                   java.lang.String value)

      Sets the value of the top-level stylesheet parameter. This value must be a valid XPath expression; string literal values have to be explicitly quoted. This method is a no-op if a stylesheet is not registered.
      Parameters:
      `name` - parameter name

      `value` - parameter value as an `XPATH` expression

    <!-- -->

    - #### removeXSLTParam

          public void removeXSLTParam(java.lang.String name)

      Removes the value of a top-level stylesheet parameter. This method is a no-op if a stylesheet is not registered.
      Parameters:
      `name` - parameter name

    <!-- -->

    - #### setCommitBatch

          public void setCommitBatch(int size)

      Sets the commit batch size, or the number of records inserted before a commit. If `size < 1` or the session is in "auto-commit" mode, no explicit commits are made. The default `size` is `0`.
      Parameters:
      `size` - commit batch size

    <!-- -->

    - #### setSQLToXMLNameEscaping

          public void setSQLToXMLNameEscaping(boolean flag)

      Determines whether to turn on XML tag escaping for SQL object names, to ensure conversion to valid XML identifiers.
      Parameters:
      `flag` - `TRUE` to turn on SQL to XML escaping

    <!-- -->

    - #### setIgnoreCase

          public void setIgnoreCase(boolean ignore)

      Sets the comparison mode. When driving DML (INSERT, UPDATE, DELETE) from an XML document, the XML element names and attribute names, based on XML tags, are compared to the list of column names. Using `ignore = true` causes the comparison to be case insensitive by converting both values to upper case, using the `Locale` for English (i.e., `java.util.Locale.ENGLISH`). This may affect metadata caching while creating the `OracleXMLSave` object. It can also have unexpected effects when using names that contain non-English characters (i.e., characters that are outside of the range of US ASCII).
      Parameters:
      `ignore` - ignore tag case in the XML doc?

    <!-- -->

    - #### setRowTag

          public void setRowTag(java.lang.String rowTag)

      Names the tag for the row enclosing XML element. Setting the `rowTag` to `null` means that top level elements of the document correspond to table rows.
      Parameters:
      `rowTag` - tag name

    <!-- -->

    - #### setDateFormat

          public void setDateFormat(java.lang.String mask)

      Specifies the format of dates used in the XML document. The default setting format, or date mask, is `MM/dd/yyyy HH:mm:ss`. The default override should conform to requirements of the `java.text.SimpleDateFormat` class. Setting the `mask` parameter to `null</null> or empty string sets the default mask ``OracleXMLSave.DATE_FORMAT``.`
      Parameters:
      `mask` - the date mask

    <!-- -->

    - #### createURL

          public java.net.URL createURL(java.lang.String fileName)

      Returns the URL object for a specified file or URL. If the `target` parameter is not a valid URL format, "http://..." or "file://...", tries to create a URL object of the form "file://`target`". Returns `null` if the `target` parameter is `null` or an empty string.
      Parameters:
      `fileName` - The name of the file

      Returns:
      the URL object identifiying the `target` entity

    <!-- -->

    - #### getURL

          public static java.net.URL getURL(java.lang.String target)

      Given a file name or a URL it return a URL object. If the argument passed is not in the valid URL format (e.g. http://.. or file://) then this method tried to fix the argument by pre-pending "file://" to the argument. If a `null` or an empty string are passed to it, null is returned.
      Parameters:
      `target` - file name or URL string

      Returns:
      the URL object identifiying the `target` entity

    <!-- -->

    - #### close

          public void close()

      Closes the `OracleXMLSave` object and deallocates all context associated with it.

    <!-- -->

    - #### cleanLobList

          public void cleanLobList()

      This function frees all temporary LOBs

    <!-- -->

    - #### insertXML

          public int insertXML(java.net.URL url)

      Inserts an XML document from a specified URL into a table, By default, matches element names to column names, and sets columns with missing elements in input to `null</null>. To restrict insertion to a subset of a table's columns and allow the other columns to hold a default value, use the ``setUpdateColumnList()`` method. Set the key column by a ``setKeyColumnList()`` call. For example, consider the employee table emp: TABLE emp( empno NUMBER, ename VARCHAR2(20), hiredate DATE); Now, assume that you want to insert the table using an XML document. OracleXMLSave save = new OracleXMLSave(conn, "emp"); save.insertXML(xmlDoc); // xmlDoc supplied.. save.close(); If you want to insert values only into EMPNO, HIREDATE, and SALARY and let the default values handle the rest of the columns: String insArray = new String[3]; insArray[0] = "EMPNO"; insArray[1] = "HIREDATE"; insArray[2] = "SALARY"; save.setUpdateColumnList(insArray); save.insertXML(xmlDoc); // will only insert values into EMPNO, HIREDATE, // and SALARY columns`
      Parameters:
      `url` - URL to the input XML document used to populate the table

      Returns:
      The number of rows inserted.

    <!-- -->

    - #### insertXML

          public int insertXML(java.lang.String xmlDoc)
                        throws java.io.IOException

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### insertXML

          public int insertXML(java.io.Reader xmlStream)

    <!-- -->

    - #### insertXML

          public int insertXML(java.io.InputStream xmlStream)

    <!-- -->

    - #### insertXML

          public int insertXML(Document doc)

    <!-- -->

    - #### updateXML

          public int updateXML(java.net.URL url)

      Updates the columns in a database table, based on the element values in the input XML document. Requires a key column that contains unique identifiers of rows that must be changed. By default, uses the list of key columns to match XML elements to table rows, and updates the entire row. Each row update is treated as a separate `UPDATE` transaction. To restrict update to a subset of columns and allow the other columns to hold previous values, use the `setUpdateColumnList()` method. This has the added benefit of improving performance by caching the `UPDATE` statement and batching transactions. For example, consider the employee table emp: TABLE emp( empno NUMBER, ename VARCHAR2(20), hiredate DATE); Now, assume that you want to update the table using an XML document and you want to use the values of the element EMPNO to match the right row and then only update the HIREDATE column. You can send in an XML document containing the HIREDATE value and the EMPNO value and call the updateXML() routine with the setKeyColumnList() containing the EMPNO string. OracleXMLSave save = new OracleXMLSave(conn, "emp"); String\[\] keyArray = new String\[1\]; keyArray\[0\] = "EMPNO"; // Set EMPNO as key column. save.setKeyColumnList(keyArray); // Set the key column names. String\[\] updArray = new String\[1\]; updArray\[0\] = "HIREDATE"; // Set hiredate as column to update. save.setUpdateColumnList(updArray); save.updateXML(xmlDoc); // xmlDoc supplied.. save.close();
      Parameters:
      `url` - URL to the input XML document used to update the table

      Returns:
      The number of XML row elements processed. This may not be equivalent to the number of database rows modified if the rows selected through the XML document do not uniquely identify the table rows.

    <!-- -->

    - #### updateXML

          public int updateXML(java.lang.String xmlDoc)
                        throws java.io.IOException

      Updates the table given the XML document in a string form. Requires a key column that contains unique identifiers of rows that must be changed. By default, uses the list of key columns to match XML elements to table rows, and updates the entire row. Each row update is treated as a separate `UPDATE` transaction. To restrict update to a subset of columns and allow the other columns to hold previous values, use the `setUpdateColumnList()` method. This has the added benefit of improving performance by caching the `UPDATE` statement and batching transactions.
      Parameters:
      `xmlDoc` - The string form of the XML document

      Returns:
      The number of XML row elements processed. This may not be equivalent to the number of database rows modified if the rows selected through the XML document do not uniquely identify the table rows.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### updateXML

          public int updateXML(java.io.Reader xmlStream)

      Updates the table given the XML document in a stream form. Requires a key column that contains unique identifiers of rows that must be changed. By default, uses the list of key columns to match XML elements to table rows, and updates the entire row. Each row update is treated as a separate `UPDATE` transaction. To restrict update to a subset of columns and allow the other columns to hold previous values, use the `setUpdateColumnList()` method. This has the added benefit of improving performance by caching the `UPDATE` statement and batching transactions.
      Parameters:
      `xmlStream` - The stream form of the XML document

      Returns:
      The number of XML row elements processed. This may not be equivalent to the number of database rows modified if the rows selected through the XML document do not uniquely identify the table rows.

    <!-- -->

    - #### updateXML

          public int updateXML(java.io.InputStream xmlStream)

      Updates the table given the XML document in a stream form. Requires a key column that contains unique identifiers of rows that must be changed. By default, uses the list of key columns to match XML elements to table rows, and updates the entire row. Each row update is treated as a separate `UPDATE` transaction. To restrict update to a subset of columns and allow the other columns to hold previous values, use the `setUpdateColumnList()` method. This has the added benefit of improving performance by caching the `UPDATE` statement and batching transactions.
      Parameters:
      `xmlStream` - The stream form of the XML document

      Returns:
      The number of XML row elements processed. This may not be equivalent to the number of database rows modified if the rows selected through the XML document do not uniquely identify the table rows.

    <!-- -->

    - #### updateXML

          public int updateXML(Document doc)

      Updates the table given the XML document in a DOM tree form. Requires a key column that contains unique identifiers of rows that must be changed. By default, uses the list of key columns to match XML elements to table rows, and updates the entire row. Each row update is treated as a separate `UPDATE` transaction. To restrict update to a subset of columns and allow the other columns to hold previous values, use the `setUpdateColumnList()` method. This has the added benefit of improving performance by caching the `UPDATE` statement and batching transactions.
      Parameters:
      `doc` - The DOM tree form of the XML document

      Returns:
      The number of XML row elements processed. This may not be equivalent to the number of database rows modified if the rows selected through the XML document do not uniquely identify the table rows.

    <!-- -->

    - #### deleteXML

          public int deleteXML(java.net.URL url)

      Deletes rows from a table based on element values of the input XML document. By default, matches all XML element values with corresponding column names. Each row deletion is treated as a separate `DELETE` transaction. You can use a partial matching approach and limit the number of elements used to identify a row by using the `setKeyColumnList()` method. This has the added benefit of improving performance by caching the `DELETE` statement and batching transactions. For example, consider the employee table emp: TABLE emp( empno NUMBER, ename VARCHAR2(20), hiredate DATE); Now, you want to delete the rows in the table using an XML document and you want to identify the row based on the EMPNO value. You can send in an XML document containing the EMPNO value and call the deleteXML() routine with the setKeyColumnList() containing the EMPNO string. OracleXMLSave save = new OracleXMLSave(conn, "emp"); save.deleteXML(xmlDoc); // Deletes rows by matching all columns with the // element values in the input document. String\[\] deleteArray = new String\[1\]; deleteArray\[0\] = "EMPNO"; save.setKeyColumnList(deleteArray); // Set the key columns. save.deleteXML(xmlDoc); // only deletes rows by matching the EMPNO values
      Parameters:
      `url` - URL to the XML document used to identify rows for deletion from the table

      Returns:
      The number of XML row elements processed. This may not be equivalent to the number of database rows deleted if the rows selected through the XML document do not uniquely identify the table rows.

    <!-- -->

    - #### deleteXML

          public int deleteXML(java.lang.String xmlDoc)
                        throws java.io.IOException

      Deletes the rows in the table based on the XML document. By default, matches all XML element values with corresponding column names. Each row deletion is treated as a separate `DELETE` transaction. You can use a partial matching approach and limit the number of elements used to identify a row by using the `setKeyColumnList()` method. This has the added benefit of improving performance by caching the `DELETE` statement and batching transactions.
      Parameters:
      `xmlDoc` - The XML document in String form

      Returns:
      The number of XML row elements processed. This may not be equivalent to the number of database rows deleted if the rows selected through the XML document do not uniquely identify the table rows.

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### deleteXML

          public int deleteXML(java.io.Reader xmlStream)

      Deletes the rows in the table based on the XML document. By default, matches all XML element values with corresponding column names. Each row deletion is treated as a separate `DELETE` transaction. You can use a partial matching approach and limit the number of elements used to identify a row by using the `setKeyColumnList()` method. This has the added benefit of improving performance by caching the `DELETE` statement and batching transactions.
      Parameters:
      `xmlStream` - The XML document in Stream form

      Returns:
      The number of XML row elements processed. This may not be equivalent to the number of database rows deleted if the rows selected through the XML document do not uniquely identify the table rows.

    <!-- -->

    - #### deleteXML

          public int deleteXML(java.io.InputStream xmlStream)

      Deletes the rows in the table based on the XML document. By default, matches all XML element values with corresponding column names. Each row deletion is treated as a separate `DELETE` transaction. You can use a partial matching approach and limit the number of elements used to identify a row by using the `setKeyColumnList()` method. This has the added benefit of improving performance by caching the `DELETE` statement and batching transactions.
      Parameters:
      `xmlStream` - The XML document in Stream form

      Returns:
      The number of XML row elements processed. This may not be equivalent to the number of database rows deleted if the rows selected through the XML document do not uniquely identify the table rows.

    <!-- -->

    - #### deleteXML

          public int deleteXML(Document doc)

      Deletes the rows in the table based on the XML document By default, matches all XML element values with corresponding column names. Each row deletion is treated as a separate `DELETE` transaction. You can use a partial matching approach and limit the number of elements used to identify a row by using the `setKeyColumnList()` method. This has the added benefit of improving performance by caching the `DELETE` statement and batching transactions.
      Parameters:
      `doc` - The XML document in DOM form

      Returns:
      The number of XML row elements processed. This may not be equivalent to the number of database rows deleted if the rows selected through the XML document do not uniquely identify the table rows.

    <!-- -->

    - #### setBatchSize

          public void setBatchSize(int size)

      Changes the batch size used during DML operations. Batching operations improves performance by reducing the overhead of individual database access read/write operations to a single one. More memory is needed to hold the statements prior to a commit, as commits occur once per batch. If a single statement fails, the entire batch is rolled back. If this behavior is unaccepatable, set `size` to `1`. The default batch size is `DEFAULT_BATCH_SIZE`.
      Parameters:
      `size` - The batch size used for all DMLs.

    <!-- -->

    - #### setKeyColumnList

          public void setKeyColumnList(java.lang.String[] keyColNames)

      Sets the list of columns used to identify table rows against XML input document elements prior to `UPDATE` and `DELETE` operations. This call is mandatory for `UPDATE`s and optional for `DELETE`s. Update and deletion based on key column values is a no-op.
      Parameters:
      `keyColNames` - The names of the list of columns that are used as keys.

    <!-- -->

    - #### setUpdateColumnList

          public void setUpdateColumnList(java.lang.String[] updColNames)

      Sets and limits the list of columns for `INSERT` and `UPDATE` operations. Only these columns will be updated, leaving other values in the record in their previous states. Only values of these columns will be added when inserting a new record, setting other values to the pre-defined table default.
      Parameters:
      `updColNames` - The string list of columns to be updated.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Class**
- **Next Class**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
