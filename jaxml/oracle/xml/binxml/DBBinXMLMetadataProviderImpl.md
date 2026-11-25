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

- **[Prev Class](DBBinXMLMetadataProvider.md)**
- **Next Class**

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

## **Class DBBinXMLMetadataProviderImpl**

- **java.lang.Object**

- - **oracle.xml.binxml.DBBinXMLMetadataProviderImpl**

<!-- -->

- **All Implemented Interfaces:**
  **[BinXMLMetadataProvider](BinXMLMetadataProvider.md), [DBBinXMLMetadataProvider](DBBinXMLMetadataProvider.md)**

  ------------------------------------------------------------------------

  **
  **

      public class DBBinXMLMetadataProviderImpl
      extends java.lang.Object
      implements DBBinXMLMetadataProvider

  **Since:**
  **release specific (what release of product did this appear in)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                                                                                  |
    |-------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                              | `associateDataConnection``(java.sql.Connection dataconn)`<br>Associates a data connection with DBBinXMLMetadataProvider.                                                |
    | `java.io.Reader`                    | `getCompiledSchema``(`[`BinXMLVocabId`](BinXMLVocabId.md)` schemaId)`<br>Fetches the schema as a binary stream from the metadata repository based on the vocabulary id. |
    | `java.io.Reader`                    | `getCompiledSchema``(java.lang.String schemaURL)`<br>Fetches the schema as a binary stream from the metadata repository based on the schema URL.                        |
    | [`BinXMLStream`](BinXMLStream.md)   | `getDTD``(`[`BinXMLVocabId`](BinXMLVocabId.md)` dtdId)`<br>Fetches the DTD as a binary stream from the metadata repository based on the vocabulary id.                  |
    | [`BinXMLStream`](BinXMLStream.md)   | `getDTD``(java.lang.String dtdURL)`<br>Fetches the DTD as a binary stream from the metadata repository based on the DTD URL.                                            |
    | [`BinXMLStream`](BinXMLStream.md)   | `getTokenSet``(long tokenId)`<br>Fetches the Token Set as a binary stream in the metadata repository based on the input token id.                                       |
    | [`BinXMLStream`](BinXMLStream.md)   | `getTokenSet``(long tokenId, boolean isNS)`<br>Fetches the Token Set as a binary stream in the metadata repository based on the namespace of the input token Id.        |
    | `boolean`                           | `isSchemaAnnotationAvailable``()`<br>Specifies whether the repository performs schema annotations or not.                                                               |
    | [`BinXMLVocabId`](BinXMLVocabId.md) | `saveCompiledSchema``(java.lang.String schemaURL)`<br>Saves the compiled schema as a binary stream in the metadata repository.                                          |
    | [`BinXMLVocabId`](BinXMLVocabId.md) | `saveDTD``(java.lang.String dtdURL)`<br>Saves the DTD as a binary stream in the metadata repository.                                                                    |
    | [`BinXMLVocabId`](BinXMLVocabId.md) | `saveSchema``(java.lang.String sschema)`<br>The repository accepts a non-annotated schema, annotates it and saves it as a binary stream in the metadata repository.     |
    | [`BinXMLVocabId`](BinXMLVocabId.md) | `saveTokenSet``(java.lang.String namespaceURL)`<br>Saves the Token Set as a binary stream in the metadata repository.                                                   |
    | `void`                              | `setConnection``(java.sql.Connection metadataconn)`<br>Sets connection to be used by DBBinXMLMetaDataProvider                                                           |
    | `void`                              | `setConnectionPool``(oracle.jdbc.pool.OracleDataSource connpool)`<br>For OCI connection TODO: mv to Oracle DB subclass                                                  |
    | `void`                              | `setConnStr``(java.lang.String connstr, java.lang.String usr, java.lang.String passwd)`<br>For Thin connection                                                          |
    | `void`                              | `setDriver``(java.sql.Driver driver)`<br>Specify database driver to be used by DBBinXMLMetadataProvider                                                                 |
    | `void`                              | `setGUID``(byte[] guid)`                                                                                                                                                |
    | `void`                              | `setURL``(java.net.URL http, java.lang.String usrname, java.lang.String passwd)`<br>For HTTP communication only or OCI driver?                                          |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.xml.binxml.[BinXMLMetadataProvider](BinXMLMetadataProvider.md)

      [`getTokenSet`](BinXMLMetadataProvider.md)

<!-- -->

- - ### Method Detail

    - #### setConnection

          public void setConnection(java.sql.Connection metadataconn)
                             throws BinXMLException,
                                    java.sql.SQLException

      Description copied from interface: [`DBBinXMLMetadataProvider`](DBBinXMLMetadataProvider.md)
      Sets connection to be used by DBBinXMLMetaDataProvider
      Specified by:
      [`setConnection`](DBBinXMLMetadataProvider.md) in interface [`DBBinXMLMetadataProvider`](DBBinXMLMetadataProvider.md)

      Parameters:
      `metadataconn` - This connection is used to store and retrieve metadata by a DBBinXMLMetadataProvider. If the associateDataConnection method is not called, this connection will also be used to store and retrieve binary data from the database.

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any non-SQL related errors

      `java.sql.SQLException` - Raised for any SQL related errors

    <!-- -->

    - #### setConnectionPool

          public void setConnectionPool(oracle.jdbc.pool.OracleDataSource connpool)
                                 throws BinXMLException,
                                        java.sql.SQLException

      For OCI connection TODO: mv to Oracle DB subclass
      Specified by:
      [`setConnectionPool`](DBBinXMLMetadataProvider.md) in interface [`DBBinXMLMetadataProvider`](DBBinXMLMetadataProvider.md)

      Parameters:
      `connpool` - OracleDataSource for metadata retrieval

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any non-SQL related errors

      `java.sql.SQLException` - Raised for any SQL related errors

    <!-- -->

    - #### setDriver

          public void setDriver(java.sql.Driver driver)

      Description copied from interface: [`DBBinXMLMetadataProvider`](DBBinXMLMetadataProvider.md)
      Specify database driver to be used by DBBinXMLMetadataProvider
      Specified by:
      [`setDriver`](DBBinXMLMetadataProvider.md) in interface [`DBBinXMLMetadataProvider`](DBBinXMLMetadataProvider.md)

      Parameters:
      `driver` - user specified driver

    <!-- -->

    - #### setURL

          public void setURL(java.net.URL http,
                             java.lang.String usrname,
                             java.lang.String passwd)
                      throws BinXMLException,
                             java.sql.SQLException

      For HTTP communication only or OCI driver? Answer from XDB: Planned, for HTTP communication only Rename it to setOCIURL()? TODO: mv to Oracle DB subclass?
      Specified by:
      [`setURL`](DBBinXMLMetadataProvider.md) in interface [`DBBinXMLMetadataProvider`](DBBinXMLMetadataProvider.md)

      Parameters:
      `http` - URL for connection

      `usrname` - user name

      `passwd` - password for user

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any non-SQL related errors

      `java.sql.SQLException` - Raised for any SQL related errors

    <!-- -->

    - #### setConnStr

          public void setConnStr(java.lang.String connstr,
                                 java.lang.String usr,
                                 java.lang.String passwd)
                          throws BinXMLException,
                                 java.sql.SQLException

      For Thin connection
      Specified by:
      [`setConnStr`](DBBinXMLMetadataProvider.md) in interface [`DBBinXMLMetadataProvider`](DBBinXMLMetadataProvider.md)

      Parameters:
      `connstr` - connection string

      `usr` - user name

      `passwd` - password for user

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any non-SQL related errors

      `java.sql.SQLException` - Raised for any SQL related errors

    <!-- -->

    - #### associateDataConnection

          public void associateDataConnection(java.sql.Connection dataconn)
                                       throws BinXMLException

      Description copied from interface: [`DBBinXMLMetadataProvider`](DBBinXMLMetadataProvider.md)
      Associates a data connection with DBBinXMLMetadataProvider. May be called more than once for associating multiple data connections. If this API is not called, then data is stored and retrieved using the Connection specified by setConnection().
      Specified by:
      [`associateDataConnection`](DBBinXMLMetadataProvider.md) in interface [`DBBinXMLMetadataProvider`](DBBinXMLMetadataProvider.md)

      Parameters:
      `dataconn` - JDBC connection used for storage and retrieval of Binary XML data.

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### isSchemaAnnotationAvailable

          public boolean isSchemaAnnotationAvailable()
                                              throws BinXMLException

      Specifies whether the repository performs schema annotations or not. DBBinXMLMetadataProvider) will return true The Binary XML Processor calls this API to determine whether to call saveSchema for registering a schema in the repository where the annotations are performed by the repository or call saveCompiledSchema for saving a already annotated schema to the repository.
      Specified by:
      [`isSchemaAnnotationAvailable`](BinXMLMetadataProvider.md) in interface [`BinXMLMetadataProvider`](BinXMLMetadataProvider.md)

      Returns:
      always returns true since XDB supports schema annotations while saving

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getCompiledSchema

          public java.io.Reader getCompiledSchema(BinXMLVocabId schemaId)
                                           throws BinXMLException

      Fetches the schema as a binary stream from the metadata repository based on the vocabulary id.
      Specified by:
      [`getCompiledSchema`](BinXMLMetadataProvider.md) in interface [`BinXMLMetadataProvider`](BinXMLMetadataProvider.md)

      Parameters:
      `schemaId` - - vocabulary id of the schema to be fetched

      Returns:
      binary stream version of the compiled schema doc

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getCompiledSchema

          public java.io.Reader getCompiledSchema(java.lang.String schemaURL)
                                           throws BinXMLException

      Fetches the schema as a binary stream from the metadata repository based on the schema URL.
      Specified by:
      [`getCompiledSchema`](BinXMLMetadataProvider.md) in interface [`BinXMLMetadataProvider`](BinXMLMetadataProvider.md)

      Parameters:
      `schemaURL` - - URL of the schema to be fetched

      Returns:
      binary stream version of the compiled schema doc

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### saveSchema

          public BinXMLVocabId saveSchema(java.lang.String sschema)
                                   throws BinXMLException

      The repository accepts a non-annotated schema, annotates it and saves it as a binary stream in the metadata repository.
      Specified by:
      [`saveSchema`](BinXMLMetadataProvider.md) in interface [`BinXMLMetadataProvider`](BinXMLMetadataProvider.md)

      Parameters:
      `sschema` - - String of the schema to be saved

      Returns:
      the vocabulary id of the saved schema

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### saveCompiledSchema

          public BinXMLVocabId saveCompiledSchema(java.lang.String schemaURL)
                                           throws BinXMLException

      Saves the compiled schema as a binary stream in the metadata repository.
      Specified by:
      [`saveCompiledSchema`](BinXMLMetadataProvider.md) in interface [`BinXMLMetadataProvider`](BinXMLMetadataProvider.md)

      Parameters:
      `schemaURL` - - URL of the schema to be saved

      Returns:
      the vocabulary id saved schema

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getDTD

          public BinXMLStream getDTD(BinXMLVocabId dtdId)
                              throws BinXMLException

      Fetches the DTD as a binary stream from the metadata repository based on the vocabulary id.
      Specified by:
      [`getDTD`](BinXMLMetadataProvider.md) in interface [`BinXMLMetadataProvider`](BinXMLMetadataProvider.md)

      Parameters:
      `dtdId` - - vocabulary id of the DTD to be fetched

      Returns:
      binary stream version of the DTD

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getDTD

          public BinXMLStream getDTD(java.lang.String dtdURL)
                              throws BinXMLException

      Fetches the DTD as a binary stream from the metadata repository based on the DTD URL.
      Specified by:
      [`getDTD`](BinXMLMetadataProvider.md) in interface [`BinXMLMetadataProvider`](BinXMLMetadataProvider.md)

      Parameters:
      `dtdURL` - - URL of the DTD to be fetched

      Returns:
      binary stream version of the DTD

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### saveDTD

          public BinXMLVocabId saveDTD(java.lang.String dtdURL)
                                throws BinXMLException

      Saves the DTD as a binary stream in the metadata repository.
      Specified by:
      [`saveDTD`](BinXMLMetadataProvider.md) in interface [`BinXMLMetadataProvider`](BinXMLMetadataProvider.md)

      Parameters:
      `dtdURL` - - URL of the DTD to be saved

      Returns:
      the vocabulary id of the DTD to be saved

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getTokenSet

          public BinXMLStream getTokenSet(long tokenId)
                                   throws BinXMLException

      Description copied from interface: [`BinXMLMetadataProvider`](BinXMLMetadataProvider.md)
      Fetches the Token Set as a binary stream in the metadata repository based on the input token id.
      Specified by:
      [`getTokenSet`](BinXMLMetadataProvider.md) in interface [`BinXMLMetadataProvider`](BinXMLMetadataProvider.md)

      Parameters:
      `tokenId` - - token Id contained in the Token Set to be fetched

      Returns:
      getTokenSet(tokenId, false);

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getTokenSet

          public BinXMLStream getTokenSet(long tokenId,
                                          boolean isNS)
                                   throws BinXMLException

      Fetches the Token Set as a binary stream in the metadata repository based on the namespace of the input token Id.
      Specified by:
      [`getTokenSet`](BinXMLMetadataProvider.md) in interface [`BinXMLMetadataProvider`](BinXMLMetadataProvider.md)

      Parameters:
      `tokenId` - - token Id contained in the Token Set to be fetched

      `isNS` - - if this token is a namespace decl, then true, otherwise false

      Returns:
      binary stream version of the Token Set

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### saveTokenSet

          public BinXMLVocabId saveTokenSet(java.lang.String namespaceURL)
                                     throws BinXMLException

      Saves the Token Set as a binary stream in the metadata repository.
      Specified by:
      [`saveTokenSet`](BinXMLMetadataProvider.md) in interface [`BinXMLMetadataProvider`](BinXMLMetadataProvider.md)

      Parameters:
      `namespaceURL` - - namespace URL of the Token Set to be saved

      Returns:
      vocabulary id of the Token Set saved in the metadata repository

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### setGUID

          public void setGUID(byte[] guid)

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

- **[Prev Class](DBBinXMLMetadataProvider.md)**
- **Next Class**

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
