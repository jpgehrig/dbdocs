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
- **[Next Class](DBAccessBeanInfo.md)**

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

**oracle.xml.transviewer**

## **Class DBAccess**

- **java.lang.Object**

- - **oracle.xml.transviewer.DBAccess**

<!-- -->

-

  ------------------------------------------------------------------------

  **Deprecated. **
  **Please use oracle.xml.dbaccess.DBAccess**
  **
  **

      public class DBAccess
      extends java.lang.Object

  **Maintains CLOB tables that can hold multiple XML and text documents. Each table is created using the statement: CREATE TABLE tablename FILENAME CHAR( 16) UNIQUE, FILEDATA CLOB) LOB(FILEDATA) STORE AS (DISABLE STORAGE IN ROW). Each XML (or text) document is stored as a row in the table and the FILENAME field holds a unique string that is used as a key to retrieve, update or delete the row. The document text is stored in the FILEDATA field that is a CLOB object. The class creates and deletes CLOB tables, list a CLOB table content and also add, replace or delete text documents in this CLOB tables.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description         |
    |-------------------------------------|
    | `DBAccess``()`<br>Deprecated. <br>  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type    | Method and Description                                                                                                                                                                 |
    |----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`            | `createBLOBTable``(java.sql.Connection con, java.lang.String tablename)`<br>Deprecated. <br>Create BLOB table                                                                          |
    | `boolean`            | `createXMLTable``(java.sql.Connection con, java.lang.String tablename)`<br>Deprecated. <br>Create XML table                                                                            |
    | `boolean`            | `deleteBLOBName``(java.sql.Connection con, java.lang.String tablename, java.lang.String xmlname)`<br>Deprecated. <br>Delete binary file from BLOB table                                |
    | `boolean`            | `deleteXMLName``(java.sql.Connection con, java.lang.String tablename, java.lang.String xmlname)`<br>Deprecated. <br>Delete file from XML table                                         |
    | `boolean`            | `dropBLOBTable``(java.sql.Connection con, java.lang.String tablename)`<br>Deprecated. <br>Delete BLOB table                                                                            |
    | `boolean`            | `dropXMLTable``(java.sql.Connection con, java.lang.String tablename)`<br>Deprecated. <br>Delete XML table                                                                              |
    | `byte[]`             | `getBLOBData``(java.sql.Connection con, java.lang.String tablename, java.lang.String xmlname)`<br>Deprecated. <br>Retrieve binary file from BLOB table                                 |
    | `int`                | `getNameSize``()`<br>Deprecated. <br>Returns the size of the field where the filename is kept.                                                                                         |
    | `java.lang.String`   | `getXMLData``(java.sql.Connection con, java.lang.String tablename, java.lang.String xmlname)`<br>Deprecated. <br>Retrieve text file from XML table                                     |
    | `java.lang.String[]` | `getXMLNames``(java.sql.Connection con, java.lang.String tablename)`<br>Deprecated. <br>Returns all file names in XML table                                                            |
    | `java.lang.String[]` | `getXMLTableNames``(java.sql.Connection con, java.lang.String tablePrefix)`<br>Deprecated. <br>Gets all XML tables with names starting with a given string                             |
    | `boolean`            | `insertBLOBData``(java.sql.Connection con, java.lang.String tablename, java.lang.String xmlname, byte[] xmldata)`<br>Deprecated. <br>Inserts binary file as a row in BLOB table        |
    | `boolean`            | `insertXMLData``(java.sql.Connection con, java.lang.String tablename, java.lang.String xmlname, java.lang.String xmldata)`<br>Deprecated. <br>Inserts text file as a row in XML table  |
    | `boolean`            | `isXMLTable``(java.sql.Connection con, java.lang.String tablename)`<br>Deprecated. <br>Check if the table is XML table.                                                                |
    | `boolean`            | `replaceXMLData``(java.sql.Connection con, java.lang.String tablename, java.lang.String xmlname, java.lang.String xmldata)`<br>Deprecated. <br>Replace text file as a row in XML table |
    | `boolean`            | `xmlTableExists``(java.sql.Connection con, java.lang.String tablename)`<br>Deprecated. <br>Checks if the XML table exists                                                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DBAccess

          public DBAccess()

      Deprecated. 

  <!-- -->

  - ### Method Detail

    - #### getNameSize

          public int getNameSize()

      Deprecated. 
      Returns the size of the field where the filename is kept.
      Returns:
      filename size

    <!-- -->

    - #### isXMLTable

          public boolean isXMLTable(java.sql.Connection con,
                                    java.lang.String tablename)
                             throws java.lang.Exception

      Deprecated. 
      Check if the table is XML table.
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name to test

      Returns:
      true if this is XML table

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getXMLTableNames

          public java.lang.String[] getXMLTableNames(java.sql.Connection con,
                                                     java.lang.String tablePrefix)
                                              throws java.lang.Exception

      Deprecated. 
      Gets all XML tables with names starting with a given string
      Parameters:
      `con` - - the Connection object

      `tablePrefix` - - table prefix string

      Returns:
      array of all XML tables that begin with tablePrefix

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### insertXMLData

          public boolean insertXMLData(java.sql.Connection con,
                                       java.lang.String tablename,
                                       java.lang.String xmlname,
                                       java.lang.String xmldata)
                                throws java.sql.SQLException,
                                       java.io.IOException

      Deprecated. 
      Inserts text file as a row in XML table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      `xmlname` - - the file name

      `xmldata` - - string with the file data

      Returns:
      true if successfull

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### insertBLOBData

          public boolean insertBLOBData(java.sql.Connection con,
                                        java.lang.String tablename,
                                        java.lang.String xmlname,
                                        byte[] xmldata)
                                 throws java.sql.SQLException,
                                        java.io.IOException

      Deprecated. 
      Inserts binary file as a row in BLOB table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      `xmlname` - - the file name

      `xmldata` - - byte array with file data

      Returns:
      true if successfull

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### replaceXMLData

          public boolean replaceXMLData(java.sql.Connection con,
                                        java.lang.String tablename,
                                        java.lang.String xmlname,
                                        java.lang.String xmldata)
                                 throws java.lang.Exception

      Deprecated. 
      Replace text file as a row in XML table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      `xmlname` - - the file name

      `xmldata` - - string with the file data

      Returns:
      true if successfull

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### xmlTableExists

          public boolean xmlTableExists(java.sql.Connection con,
                                        java.lang.String tablename)
                                 throws java.lang.Exception

      Deprecated. 
      Checks if the XML table exists
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      Returns:
      true if the table exists

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### dropXMLTable

          public boolean dropXMLTable(java.sql.Connection con,
                                      java.lang.String tablename)
                               throws java.lang.Exception

      Deprecated. 
      Delete XML table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      Returns:
      true if successfull

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### dropBLOBTable

          public boolean dropBLOBTable(java.sql.Connection con,
                                       java.lang.String tablename)
                                throws java.lang.Exception

      Deprecated. 
      Delete BLOB table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      Returns:
      true if successfull

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### createXMLTable

          public boolean createXMLTable(java.sql.Connection con,
                                        java.lang.String tablename)
                                 throws java.lang.Exception

      Deprecated. 
      Create XML table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      Returns:
      true if successfull

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### createBLOBTable

          public boolean createBLOBTable(java.sql.Connection con,
                                         java.lang.String tablename)
                                  throws java.lang.Exception

      Deprecated. 
      Create BLOB table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      Returns:
      true if successfull

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getXMLNames

          public java.lang.String[] getXMLNames(java.sql.Connection con,
                                                java.lang.String tablename)
                                         throws java.lang.Exception

      Deprecated. 
      Returns all file names in XML table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      Returns:
      String array with all file names in this table

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getXMLData

          public java.lang.String getXMLData(java.sql.Connection con,
                                             java.lang.String tablename,
                                             java.lang.String xmlname)
                                      throws java.sql.SQLException

      Deprecated. 
      Retrieve text file from XML table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      `xmlname` - - the file name

      Returns:
      file as a string

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getBLOBData

          public byte[] getBLOBData(java.sql.Connection con,
                                    java.lang.String tablename,
                                    java.lang.String xmlname)
                             throws java.sql.SQLException

      Deprecated. 
      Retrieve binary file from BLOB table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      `xmlname` - - the file name

      Returns:
      file as a byte array

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### deleteBLOBName

          public boolean deleteBLOBName(java.sql.Connection con,
                                        java.lang.String tablename,
                                        java.lang.String xmlname)
                                 throws java.lang.Exception

      Deprecated. 
      Delete binary file from BLOB table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      `xmlname` - - the file name

      Returns:
      true if successfull

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### deleteXMLName

          public boolean deleteXMLName(java.sql.Connection con,
                                       java.lang.String tablename,
                                       java.lang.String xmlname)
                                throws java.lang.Exception

      Deprecated. 
      Delete file from XML table
      Parameters:
      `con` - - the Connection object

      `tablename` - - the table name

      `xmlname` - - the file name

      Returns:
      true if successfull

      Throws:
      `java.lang.Exception`

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
- **[Next Class](DBAccessBeanInfo.md)**

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
