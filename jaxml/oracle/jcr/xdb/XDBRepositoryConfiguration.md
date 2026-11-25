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

- **[Prev Class](JDBCConnectionCredentials.md)**
- **[Next Class](XDBRepositoryConfigurationFactory.md)**

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

**oracle.jcr.xdb**

## **Class XDBRepositoryConfiguration**

- **java.lang.Object**

- - **oracle.jcr.xdb.XDBRepositoryConfiguration**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable, javax.naming.Referenceable, [OracleRepositoryConfiguration](../OracleRepositoryConfiguration.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **XDBRepositoryConfiguration specifies the configuration of an OracleRepository connected to an XML DB repository using the XML DB Content Connector.**
  **An XDBRepositoryConfiguration object is contained by a Repository object. When you deploy a JCR application, you can configure the Repository object and its contained XDBRepositoryConfiguration object for the application, then store the Repository object in a JNDI directory for retrieval at runtime.**

  **The XDBRepositoryConfiguration object also records JCR's namespace registry and the list of XML schemas registered for use in JCR. This configuration data is updated using the methods of OracleNamespaceRegistry and OracleNodeTypeManager. Changes made using these methods take immediate effect within this Repository object. To make these changes permanent, rebind the Repository object into the JNDI directory.**

  **
  **

      public class XDBRepositoryConfiguration
      extends java.lang.Object
      implements OracleRepositoryConfiguration

  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                    |
    |-------------------|--------------------------------------------------------------------------|
    | `static byte`     | `TRANSACTIONMODE_EXPLICIT`<br>Deprecated. <br>Explicit transaction mode. |
    | `static byte`     | `TRANSACTIONMODE_IMPLICIT`<br>Deprecated. <br>Implicit transaction mode. |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                   |
    |-----------------------------------------------------------------------------------------------|
    | `XDBRepositoryConfiguration``()`<br>Deprecated. <br>Constructs an XDBRepositoryConfiguration. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type        | Method and Description                                                                                                                                 |
    |--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `javax.sql.DataSource`   | `getDataSource``()`<br>Deprecated. <br>Gets the JDBC data source for the XML DB repository.                                                            |
    | `java.lang.String`       | `getDescriptor``(java.lang.String key)`<br>Deprecated. <br>Gets the value of the specified descriptor key.                                             |
    | `java.lang.String[]`     | `getDescriptorKeys``()`<br>Deprecated. <br>Gets the keys of the descriptors contributed to the OracleRepository by this OracleRepositoryConfiguration. |
    | `javax.naming.Reference` | `getReference``()`<br>Deprecated.                                                                                                                      |
    | `byte`                   | `getTransactionMode``()`<br>Deprecated. <br>Gets the transaction mode.                                                                                 |
    | `void`                   | `setDataSource``(javax.sql.DataSource dataSource)`<br>Deprecated. <br>Sets the JDBC data source for the XML DB repository.                             |
    | `void`                   | `setTransactionMode``(byte mode)`<br>Deprecated. <br>Sets the transaction mode.                                                                        |
    | `java.lang.String`       | `toString``()`<br>Deprecated.                                                                                                                          |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### TRANSACTIONMODE_IMPLICIT

          public static final byte TRANSACTIONMODE_IMPLICIT

      Deprecated. 
      Implicit transaction mode.
      In this mode, calls to the `save` methods of `Item` and `Session` and the `copy`, `clone`, `move`, `restore`, `getImportContentHandler`, and `import` methods of `Workspace` are implicitly committted. When these methods are invoked, a database savepoint is created and the changes are applied to the database. If all changes succeed, the transaction is committed. If any change fails, the transaction is rolled back to the savepoint.

      This is the default transaction mode.

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TRANSACTIONMODE_EXPLICIT

          public static final byte TRANSACTIONMODE_EXPLICIT

      Deprecated. 
      Explicit transaction mode.
      In this mode, calls to the `save` methods of `Item` and `Session` and the `copy`, `clone`, `move`, `restore`, `getImportContentHandler`, and `import` methods of `Workspace` must be explicitly committed. When these methods are invoked, a database savepoint is created and the changes posted to the database. If all changes succeed, the savepoint is released without committing the transaction. If any change fails, the transaction is rolled back to the savepoint.

      The application (or J2EE container) is responsible for committing or rolling back the transaction. For local transactions, this can be performed using the `commit` and `rollback` methods of `OracleWorkspace`. If the JCR session was created using `JDBCConnectionCredentials`, this can be equivalently performed using the JDBC `commit` and `rollback` methods.

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### XDBRepositoryConfiguration

          public XDBRepositoryConfiguration()
                                     throws RepositoryException

      Deprecated. 
      Constructs an XDBRepositoryConfiguration.
      Throws:
      [`RepositoryException`](../../../javax/jcr/RepositoryException.md) - if the operation fails

  <!-- -->

  - ### Method Detail

    - #### getDescriptorKeys

          public java.lang.String[] getDescriptorKeys()

      Deprecated. 
      Gets the keys of the descriptors contributed to the OracleRepository by this OracleRepositoryConfiguration.
      Thd returned keys may be a subset of those returned by OracleRepository `getDescriptorKeys`.

      Specified by:
      [`getDescriptorKeys`](../OracleRepositoryConfiguration.md) in interface [`OracleRepositoryConfiguration`](../OracleRepositoryConfiguration.md)

      Returns:
      the keys

    <!-- -->

    - #### getDescriptor

          public java.lang.String getDescriptor(java.lang.String key)

      Deprecated. 
      Gets the value of the specified descriptor key.
      Specified by:
      [`getDescriptor`](../OracleRepositoryConfiguration.md) in interface [`OracleRepositoryConfiguration`](../OracleRepositoryConfiguration.md)

      Parameters:
      `key` - a key in the set returned by `getDescriptorKeys`

      Returns:
      the value, or null if the key is not found

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Deprecated. 
      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### getDataSource

          public javax.sql.DataSource getDataSource()

      Deprecated. 
      Gets the JDBC data source for the XML DB repository.
      Returns:
      the data source

    <!-- -->

    - #### setDataSource

          public void setDataSource(javax.sql.DataSource dataSource)

      Deprecated. 
      Sets the JDBC data source for the XML DB repository.
      Parameters:
      `dataSource` - the data source; required

    <!-- -->

    - #### getTransactionMode

          public byte getTransactionMode()

      Deprecated. 
      Gets the transaction mode.
      Returns:
      the mode, either `TRANSACTIONMODE_IMPLICIT` (default) or `TRANSACTIONMODE_EXPLICIT`

    <!-- -->

    - #### setTransactionMode

          public void setTransactionMode(byte mode)

      Deprecated. 
      Sets the transaction mode.
      Changes to the transaction mode apply to all sessions created by the Repository, both existing and subsequently created.

      Parameters:
      `mode` - the mode, either `TRANSACTIONMODE_IMPLICIT` or `TRANSACTIONMODE_EXPLICIT`

    <!-- -->

    - #### getReference

          public javax.naming.Reference getReference()
                                              throws javax.naming.NamingException

      Deprecated. 
      Specified by:
      `getReference` in interface `javax.naming.Referenceable`

      Throws:
      `javax.naming.NamingException`

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

- **[Prev Class](JDBCConnectionCredentials.md)**
- **[Next Class](XDBRepositoryConfigurationFactory.md)**

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
