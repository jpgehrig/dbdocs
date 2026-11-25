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

- **[Prev Class](BinXMLVocabId.md)**
- **[Next Class](DBBinXMLMetadataProviderImpl.md)**

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

**oracle.xml.binxml**

## **Interface DBBinXMLMetadataProvider**

- **All Superinterfaces:**
  **[BinXMLMetadataProvider](BinXMLMetadataProvider.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[DBBinXMLMetadataProviderImpl](DBBinXMLMetadataProviderImpl.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface DBBinXMLMetadataProvider
      extends BinXMLMetadataProvider

  **The interface implements the BinXMLMetadataProvider interface. This interface defines interfaces to implement Oracle Database 11g as the backend metadata provider for a BinXMLProcessor. It defines APIs to establish a connection with the Oracle DB.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                           |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `associateDataConnection``(java.sql.Connection dataconn)`<br>Associates a data connection with DBBinXMLMetadataProvider.         |
    | `void`            | `setConnection``(java.sql.Connection metadataconn)`<br>Sets connection to be used by DBBinXMLMetaDataProvider                    |
    | `void`            | `setConnectionPool``(oracle.jdbc.pool.OracleDataSource connpool)`<br>Sets connection pool to be used by DBBinXMLMetadataProvider |
    | `void`            | `setConnStr``(java.lang.String connstr, java.lang.String usr, java.lang.String passwd)`<br>Used for setting up thin connection.  |
    | `void`            | `setDriver``(java.sql.Driver driver)`<br>Specify database driver to be used by DBBinXMLMetadataProvider                          |
    | `void`            | `setURL``(java.net.URL http, java.lang.String usrname, java.lang.String passwd)`<br>Used for setting up OCI connection           |

    - ### Methods inherited from interface oracle.xml.binxml.[BinXMLMetadataProvider](BinXMLMetadataProvider.md)

      [`getCompiledSchema`](BinXMLMetadataProvider.md)`, `[`getCompiledSchema`](BinXMLMetadataProvider.md)`, `[`getDTD`](BinXMLMetadataProvider.md)`, `[`getDTD`](BinXMLMetadataProvider.md)`, `[`getTokenSet`](BinXMLMetadataProvider.md)`, `[`getTokenSet`](BinXMLMetadataProvider.md)`, `[`getTokenSet`](BinXMLMetadataProvider.md)`, `[`isSchemaAnnotationAvailable`](BinXMLMetadataProvider.md)`, `[`saveCompiledSchema`](BinXMLMetadataProvider.md)`, `[`saveDTD`](BinXMLMetadataProvider.md)`, `[`saveSchema`](BinXMLMetadataProvider.md)`, `[`saveTokenSet`](BinXMLMetadataProvider.md)

<!-- -->

- - ### Method Detail

    - #### setConnection

          void setConnection(java.sql.Connection metadataconn)
                      throws BinXMLException,
                             java.sql.SQLException

      Sets connection to be used by DBBinXMLMetaDataProvider
      Parameters:
      `metadataconn` - This connection is used to store and retrieve metadata by a DBBinXMLMetadataProvider. If the associateDataConnection method is not called, this connection will also be used to store and retrieve binary data from the database.

      Throws:
      `java.sql.SQLException` - Raised for any SQL related errors

      [`BinXMLException`](BinXMLException.md) - Raised for any non-SQL related errors

    <!-- -->

    - #### setConnectionPool

          void setConnectionPool(oracle.jdbc.pool.OracleDataSource connpool)
                          throws BinXMLException,
                                 java.sql.SQLException

      Sets connection pool to be used by DBBinXMLMetadataProvider
      Parameters:
      `connpool` - OracleDataSource for metadata retrieval

      Throws:
      `java.sql.SQLException` - Raised for any SQL related errors

      [`BinXMLException`](BinXMLException.md) - Raised for any non-SQL related errors

    <!-- -->

    - #### setDriver

          void setDriver(java.sql.Driver driver)
                  throws BinXMLException

      Specify database driver to be used by DBBinXMLMetadataProvider
      Parameters:
      `driver` - user specified driver

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### setURL

          void setURL(java.net.URL http,
                      java.lang.String usrname,
                      java.lang.String passwd)
               throws BinXMLException,
                      java.sql.SQLException

      Used for setting up OCI connection
      Parameters:
      `http` - URL for connection

      `usrname` - user name

      `passwd` - password for user

      Throws:
      `java.sql.SQLException` - Raised for any SQL related errors

      [`BinXMLException`](BinXMLException.md) - Raised for any non-SQL related errors

    <!-- -->

    - #### setConnStr

          void setConnStr(java.lang.String connstr,
                          java.lang.String usr,
                          java.lang.String passwd)
                   throws BinXMLException,
                          java.sql.SQLException

      Used for setting up thin connection.
      Parameters:
      `connstr` - connection string

      `usr` - user name

      `passwd` - password for user

      Throws:
      `java.sql.SQLException` - Raised for any SQL related errors

      [`BinXMLException`](BinXMLException.md) - Raised for any non-SQL related errors

    <!-- -->

    - #### associateDataConnection

          void associateDataConnection(java.sql.Connection dataconn)
                                throws BinXMLException

      Associates a data connection with DBBinXMLMetadataProvider. May be called more than once for associating multiple data connections. If this API is not called, then data is stored and retrieved using the Connection specified by setConnection().
      Parameters:
      `dataconn` - JDBC connection used for storage and retrieval of Binary XML data.

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

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

- **[Prev Class](BinXMLVocabId.md)**
- **[Next Class](DBBinXMLMetadataProviderImpl.md)**

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
