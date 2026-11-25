Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Class**
- **[Next Class](XMLDBAccessBeanInfo.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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

**oracle.xml.xmldbaccess**

## **Class XMLDBAccess**

- **java.lang.Object**

- - **[oracle.xml.dbaccess.DBAccess](../dbaccess/DBAccess.md)**

  - - **oracle.xml.xmldbaccess.XMLDBAccess**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class XMLDBAccess
      extends DBAccess

  **This Bean is a simple extension of the DBAccess bean to support the XMLType Functionality that was introduced as a part of Oracle 9i database This bean lets user to create XMLType tables and store XML documents. The XMLDocuments are stored as rows in the database table as an XMLType type. This class also provides methods to list, delete or retrieve XMLtype tables and data. The table is created using the SQL statement CREATE TABLE (FILENAME CHAR( ) UNIQUE, FILEDATA sys.XMLType);**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `XMLDBAccess``()`           |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type    | Method and Description                                                                                                                                                                                              |
    |----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`            | `createXMLTypeTable``(java.sql.Connection con, java.lang.String tablename)`<br>Create an XMLType table                                                                                                              |
    | `java.sql.Clob`      | `getXMLTypeClob``(java.sql.Connection con, java.lang.String tablename, java.lang.String xmlname)`<br>Retrieve text file from an XMLType table                                                                       |
    | `java.lang.String`   | `getXMLTypeData``(java.sql.Connection con, java.lang.String tablename, java.lang.String xmlname)`<br>Retrieve text file from an XMLType table                                                                       |
    | `java.lang.String[]` | `getXMLTypeTableNames``(java.sql.Connection con, java.lang.String tablePrefix)`<br>Get all XML tables with names starting with a given string                                                                       |
    | `java.sql.Clob`      | `getXMLTypeXPathCLOB``(java.sql.Connection con, java.lang.String tablename, java.lang.String xmlname, java.lang.String xpathexp)`<br>Retrieve the Clob data based on the XPATH expression from an XMLType table     |
    | `java.lang.String`   | `getXMLTypeXPathTextData``(java.sql.Connection con, java.lang.String tablename, java.lang.String xmlname, java.lang.String xpathexp)`<br>Retrieve the text data based on the XPATH expression from an XMLType table |
    | `boolean`            | `insertXMLTypeData``(java.sql.Connection con, java.lang.String tablename, java.lang.String xmlname, java.lang.String xmldata)`<br>Inserts text file as a row in an XMLType table                                    |
    | `boolean`            | `isXMLTypeTable``(java.sql.Connection con, java.lang.String tablename)`<br>Check if the table is an XMLType table.                                                                                                  |
    | `boolean`            | `replaceXMLTypeData``(java.sql.Connection con, java.lang.String tablename, java.lang.String xmlname, java.lang.String xmldata)`<br>Replace text file as a row in an XMLType table                                   |

    - ### Methods inherited from class oracle.xml.dbaccess.[DBAccess](../dbaccess/DBAccess.md)

      [`createBLOBTable`](../dbaccess/DBAccess.md)`, `[`createXMLTable`](../dbaccess/DBAccess.md)`, `[`deleteBLOBName`](../dbaccess/DBAccess.md)`, `[`deleteXMLName`](../dbaccess/DBAccess.md)`, `[`dropBLOBTable`](../dbaccess/DBAccess.md)`, `[`dropXMLTable`](../dbaccess/DBAccess.md)`, `[`getBLOBData`](../dbaccess/DBAccess.md)`, `[`getNameSize`](../dbaccess/DBAccess.md)`, `[`getXMLData`](../dbaccess/DBAccess.md)`, `[`getXMLNames`](../dbaccess/DBAccess.md)`, `[`getXMLTableNames`](../dbaccess/DBAccess.md)`, `[`insertBLOBData`](../dbaccess/DBAccess.md)`, `[`insertXMLData`](../dbaccess/DBAccess.md)`, `[`isXMLTable`](../dbaccess/DBAccess.md)`, `[`replaceXMLData`](../dbaccess/DBAccess.md)`, `[`xmlTableExists`](../dbaccess/DBAccess.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XMLDBAccess

          public XMLDBAccess()

  <!-- -->

  - ### Method Detail

    - #### isXMLTypeTable

          public boolean isXMLTypeTable(java.sql.Connection con,
                                        java.lang.String tablename)
                                 throws java.lang.Exception

      Check if the table is an XMLType table.
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name to be tested

      Returns:
      true if this is an XMLType table

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getXMLTypeTableNames

          public java.lang.String[] getXMLTypeTableNames(java.sql.Connection con,
                                                         java.lang.String tablePrefix)
                                                  throws java.lang.Exception

      Get all XML tables with names starting with a given string
      Parameters:
      `con` - - the Connection object

      `tablePrefix` - - table prefix string

      Returns:
      \- array of all XMLType tables that begin with tablePrefix

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### createXMLTypeTable

          public boolean createXMLTypeTable(java.sql.Connection con,
                                            java.lang.String tablename)
                                     throws java.lang.Exception

      Create an XMLType table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      Returns:
      true if successful

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### insertXMLTypeData

          public boolean insertXMLTypeData(java.sql.Connection con,
                                           java.lang.String tablename,
                                           java.lang.String xmlname,
                                           java.lang.String xmldata)
                                    throws java.sql.SQLException,
                                           java.io.IOException,
                                           java.lang.NoClassDefFoundError

      Inserts text file as a row in an XMLType table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      `xmlname` - - the file name

      `xmldata` - - string with the file data

      Returns:
      true if successful

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.NoClassDefFoundError`

    <!-- -->

    - #### replaceXMLTypeData

          public boolean replaceXMLTypeData(java.sql.Connection con,
                                            java.lang.String tablename,
                                            java.lang.String xmlname,
                                            java.lang.String xmldata)
                                     throws java.lang.Exception,
                                            java.lang.NoClassDefFoundError

      Replace text file as a row in an XMLType table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      `xmlname` - - the file name

      `xmldata` - - string with the file data

      Returns:
      true if successful

      Throws:
      `java.lang.Exception`

      `java.lang.NoClassDefFoundError`

    <!-- -->

    - #### getXMLTypeData

          public java.lang.String getXMLTypeData(java.sql.Connection con,
                                                 java.lang.String tablename,
                                                 java.lang.String xmlname)
                                          throws java.sql.SQLException

      Retrieve text file from an XMLType table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      `xmlname` - - the file name

      Returns:
      file as a string

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getXMLTypeClob

          public java.sql.Clob getXMLTypeClob(java.sql.Connection con,
                                              java.lang.String tablename,
                                              java.lang.String xmlname)
                                       throws java.sql.SQLException

      Retrieve text file from an XMLType table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      `xmlname` - - the file name

      Returns:
      file as a Clob

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getXMLTypeXPathTextData

          public java.lang.String getXMLTypeXPathTextData(java.sql.Connection con,
                                                          java.lang.String tablename,
                                                          java.lang.String xmlname,
                                                          java.lang.String xpathexp)
                                                   throws java.sql.SQLException

      Retrieve the text data based on the XPATH expression from an XMLType table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      `xmlname` - - the file name

      `xpathexp` - - XPATH expression to search the XML document

      Returns:
      the data as a string

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getXMLTypeXPathCLOB

          public java.sql.Clob getXMLTypeXPathCLOB(java.sql.Connection con,
                                                   java.lang.String tablename,
                                                   java.lang.String xmlname,
                                                   java.lang.String xpathexp)
                                            throws java.sql.SQLException

      Retrieve the Clob data based on the XPATH expression from an XMLType table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      `xmlname` - - the file name

      `xpathexp` - - XPATH expression to search the XML document

      Returns:
      the data as a Clob

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

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Class**
- **[Next Class](XMLDBAccessBeanInfo.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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
