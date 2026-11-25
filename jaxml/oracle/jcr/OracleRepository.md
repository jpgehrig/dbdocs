Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](OracleNamespaceRegistry.md)**
- **[Next Class](OracleRepositoryConfiguration.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

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

**oracle.jcr**

## **Interface OracleRepository**

- **All Superinterfaces:**
  **javax.naming.Referenceable, [Repository](../../javax/jcr/Repository.md), java.io.Serializable**

  ------------------------------------------------------------------------

  **Deprecated. **
  **OracleRepository is the entry point to a content repository.**
  **Use the OracleRepositoryFactory class to create and configure an OracleRepository object. Then call `login` to create a JCR session.**

  **OracleRepository objects are both Serializable and Referenceable, allowing them to be stored in a JNDI directory instead of being created and initialized each time.**

  **
  **

      public interface OracleRepository
      extends Repository, java.io.Serializable, javax.naming.Referenceable

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                  |
    |---------------------------|------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `FRAMEWORK_VERSION_DESC`<br>Deprecated. <br>The repository descriptor key for the version of the Oracle JCR framework. |

    -

      ### **Fields inherited from interface javax.jcr.[Repository](../../javax/jcr/Repository.md)**

      **[`LEVEL_1_SUPPORTED`](../../javax/jcr/Repository.md)`, `[`LEVEL_2_SUPPORTED`](../../javax/jcr/Repository.md)`, `[`OPTION_LOCKING_SUPPORTED`](../../javax/jcr/Repository.md)`, `[`OPTION_OBSERVATION_SUPPORTED`](../../javax/jcr/Repository.md)`, `[`OPTION_QUERY_SQL_SUPPORTED`](../../javax/jcr/Repository.md)`, `[`OPTION_TRANSACTIONS_SUPPORTED`](../../javax/jcr/Repository.md)`, `[`OPTION_VERSIONING_SUPPORTED`](../../javax/jcr/Repository.md)`, `[`QUERY_XPATH_DOC_ORDER`](../../javax/jcr/Repository.md)`, `[`QUERY_XPATH_POS_INDEX`](../../javax/jcr/Repository.md)`, `[`REP_NAME_DESC`](../../javax/jcr/Repository.md)`, `[`REP_VENDOR_DESC`](../../javax/jcr/Repository.md)`, `[`REP_VENDOR_URL_DESC`](../../javax/jcr/Repository.md)`, `[`REP_VERSION_DESC`](../../javax/jcr/Repository.md)`, `[`SPEC_NAME_DESC`](../../javax/jcr/Repository.md)`, `[`SPEC_VERSION_DESC`](../../javax/jcr/Repository.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                   | Method and Description                                                                                                                                                                                                                             |
    |---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`CredentialsProvider`](CredentialsProvider.md)                     | `getCredentialsProvider``()`<br>Deprecated. <br>Gets the CredentialsProvider used to generate a Credentials object when no Credentials object is supplied to the `login` method of Repository.                                                     |
    | [`OracleRepositoryConfiguration`](OracleRepositoryConfiguration.md) | `getRepositoryConfiguration``()`<br>Deprecated. <br>Gets the configuration of this repository.                                                                                                                                                     |
    | `boolean`                                                           | `isStrictSaveRefreshBehavior``()`<br>Deprecated. <br>Gets whether the behavior of the `save` and `refresh` methods of Item conforms strictly to the JSR-170 specification.                                                                         |
    | `void`                                                              | `setCredentialsProvider``(`[`CredentialsProvider`](CredentialsProvider.md)` cp)`<br>Deprecated. <br>Sets the CredentialsProvider used to generate a Credentials object when no Credentials object is supplied to the `login` method of Repository. |
    | `void`                                                              | `setStrictSaveRefreshBehavior``(boolean strict)`<br>Deprecated. <br>Sets whether the behavior of the `save` and `refresh` methods of Item conforms strictly to the JSR-170 specification.                                                          |

    - ### Methods inherited from interface javax.jcr.[Repository](../../javax/jcr/Repository.md)

      [`getDescriptor`](../../javax/jcr/Repository.md)`, `[`getDescriptorKeys`](../../javax/jcr/Repository.md)`, `[`login`](../../javax/jcr/Repository.md)`, `[`login`](../../javax/jcr/Repository.md)`, `[`login`](../../javax/jcr/Repository.md)`, `[`login`](../../javax/jcr/Repository.md)

    <!-- -->

    - ### Methods inherited from interface javax.naming.Referenceable

      `getReference`

<!-- -->

- - ### Field Detail

    - #### FRAMEWORK_VERSION_DESC

          static final java.lang.String FRAMEWORK_VERSION_DESC

      Deprecated. 
      The repository descriptor key for the version of the Oracle JCR framework.
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getRepositoryConfiguration

          OracleRepositoryConfiguration getRepositoryConfiguration()

      Deprecated. 
      Gets the configuration of this repository.
      Returns:
      the repository configuration

    <!-- -->

    - #### getCredentialsProvider

          CredentialsProvider getCredentialsProvider()

      Deprecated. 
      Gets the CredentialsProvider used to generate a Credentials object when no Credentials object is supplied to the `login` method of Repository.
      Returns:
      the CredentialsProvider, or null if none

    <!-- -->

    - #### setCredentialsProvider

          void setCredentialsProvider(CredentialsProvider cp)

      Deprecated. 
      Sets the CredentialsProvider used to generate a Credentials object when no Credentials object is supplied to the `login` method of Repository.
      Parameters:
      `cp` - the CredentialsProvider, or null if none

    <!-- -->

    - #### isStrictSaveRefreshBehavior

          boolean isStrictSaveRefreshBehavior()

      Deprecated. 
      Gets whether the behavior of the `save` and `refresh` methods of Item conforms strictly to the JSR-170 specification.
      If true, `save` and `refresh` can only be called on nodes of type `nt:file`, `nt:folder`, and `ojcr:symbolicLink`. Calling these methods on nodes of other types will throw a ConstraintViolationException. This is the default.

      If false, `save` and `refresh` can be called on any node or property. Calling these methods on properties or nodes whose node type is not `nt:file`, `nt:folder`, or `ojcr:symbolicLink` will save or refresh the containing file, folder, or symbolic link.

      Returns:
      the behavior; see description

    <!-- -->

    - #### setStrictSaveRefreshBehavior

          void setStrictSaveRefreshBehavior(boolean strict)

      Deprecated. 
      Sets whether the behavior of the `save` and `refresh` methods of Item conforms strictly to the JSR-170 specification.
      If true, `save` and `refresh` can only be called on nodes of type `nt:file`, `nt:folder`, and `ojcr:symbolicLink`. Calling these methods on nodes of other types will throw a ConstraintViolationException. This is the default.

      If false, `save` and `refresh` can be called on any node or property. Calling these methods on properties or nodes whose node type is not `nt:file`, `nt:folder`, or `ojcr:symbolicLink` will save or refresh the containing file, folder, or symbolic link.

      Parameters:
      `strict` - the behavior; see description

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](OracleNamespaceRegistry.md)**
- **[Next Class](OracleRepositoryConfiguration.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

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
