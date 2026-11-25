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

- **[Prev Class](ReferentialIntegrityException.md)**
- **[Next Class](RepositoryException.md)**

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

**javax.jcr**

## **Interface Repository**

- **All Known Subinterfaces:**
  **[OracleRepository](../../oracle/jcr/OracleRepository.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Repository

  **The entry point into the content repository. Represents the entry point into the content repository. Typically the object implementing this interface will be acquired from a JNDI-compatible naming and directory service.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                    |
    |---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `LEVEL_1_SUPPORTED`<br>The presence of this key indicates that this implementation supports all level 1 features.                                        |
    | `static java.lang.String` | `LEVEL_2_SUPPORTED`<br>The presence of this key indicates that this implementation supports all level 2 features.                                        |
    | `static java.lang.String` | `OPTION_LOCKING_SUPPORTED`<br>The presence of this key indicates that this implementation supports locking.                                              |
    | `static java.lang.String` | `OPTION_OBSERVATION_SUPPORTED`<br>The presence of this key indicates that this implementation supports observation.                                      |
    | `static java.lang.String` | `OPTION_QUERY_SQL_SUPPORTED`<br>The presence of this key indicates that this implementation supports the SQL query language.                             |
    | `static java.lang.String` | `OPTION_TRANSACTIONS_SUPPORTED`<br>The presence of this key indicates that this implementation supports transactions.                                    |
    | `static java.lang.String` | `OPTION_VERSIONING_SUPPORTED`<br>The presence of this key indicates that this implementation supports versioning.                                        |
    | `static java.lang.String` | `QUERY_XPATH_DOC_ORDER`<br>The presence of this key indicates that XPath queries return results in document order.                                       |
    | `static java.lang.String` | `QUERY_XPATH_POS_INDEX`<br>The presence of this key indicates that the index position notation for same-name siblings is supported within XPath queries. |
    | `static java.lang.String` | `REP_NAME_DESC`<br>The descriptor key for the name of this repository implementation.                                                                    |
    | `static java.lang.String` | `REP_VENDOR_DESC`<br>The descriptor key for the name of the repository vendor.                                                                           |
    | `static java.lang.String` | `REP_VENDOR_URL_DESC`<br>The descriptor key for the URL of the repository vendor.                                                                        |
    | `static java.lang.String` | `REP_VERSION_DESC`<br>The descriptor key for the version of this repository implementation.                                                              |
    | `static java.lang.String` | `SPEC_NAME_DESC`<br>The descriptor key for the name of the specification that this repository implements.                                                |
    | `static java.lang.String` | `SPEC_VERSION_DESC`<br>The descriptor key for the version of the specification that this repository implements.                                          |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type       | Method and Description                                                                                                                               |
    |-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`      | `getDescriptor``(java.lang.String key)`<br>Returns the descriptor for the specified key.                                                             |
    | `java.lang.String[]`    | `getDescriptorKeys``()`<br>Returns a string array holding all descriptor keys available for this implementation.                                     |
    | [`Session`](Session.md) | `login``()`<br>Equivalent to `login(null, null)`.                                                                                                    |
    | [`Session`](Session.md) | `login``(`[`Credentials`](Credentials.md)` credentials)`<br>Equivalent to `login(credentials, null)`.                                                |
    | [`Session`](Session.md) | `login``(`[`Credentials`](Credentials.md)` credentials, java.lang.String workspaceName)`<br>Authenticates the user using the supplied `credentials`. |
    | [`Session`](Session.md) | `login``(java.lang.String workspaceName)`<br>Equivalent to `login(null, workspaceName)`.                                                             |

<!-- -->

- - ### Field Detail

    - #### SPEC_VERSION_DESC

          static final java.lang.String SPEC_VERSION_DESC

      The descriptor key for the version of the specification that this repository implements.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### SPEC_NAME_DESC

          static final java.lang.String SPEC_NAME_DESC

      The descriptor key for the name of the specification that this repository implements.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### REP_VENDOR_DESC

          static final java.lang.String REP_VENDOR_DESC

      The descriptor key for the name of the repository vendor.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### REP_VENDOR_URL_DESC

          static final java.lang.String REP_VENDOR_URL_DESC

      The descriptor key for the URL of the repository vendor.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### REP_NAME_DESC

          static final java.lang.String REP_NAME_DESC

      The descriptor key for the name of this repository implementation.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### REP_VERSION_DESC

          static final java.lang.String REP_VERSION_DESC

      The descriptor key for the version of this repository implementation.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LEVEL_1_SUPPORTED

          static final java.lang.String LEVEL_1_SUPPORTED

      The presence of this key indicates that this implementation supports all level 1 features. This key will always be present.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LEVEL_2_SUPPORTED

          static final java.lang.String LEVEL_2_SUPPORTED

      The presence of this key indicates that this implementation supports all level 2 features.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OPTION_TRANSACTIONS_SUPPORTED

          static final java.lang.String OPTION_TRANSACTIONS_SUPPORTED

      The presence of this key indicates that this implementation supports transactions.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OPTION_VERSIONING_SUPPORTED

          static final java.lang.String OPTION_VERSIONING_SUPPORTED

      The presence of this key indicates that this implementation supports versioning.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OPTION_OBSERVATION_SUPPORTED

          static final java.lang.String OPTION_OBSERVATION_SUPPORTED

      The presence of this key indicates that this implementation supports observation.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OPTION_LOCKING_SUPPORTED

          static final java.lang.String OPTION_LOCKING_SUPPORTED

      The presence of this key indicates that this implementation supports locking.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OPTION_QUERY_SQL_SUPPORTED

          static final java.lang.String OPTION_QUERY_SQL_SUPPORTED

      The presence of this key indicates that this implementation supports the SQL query language.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### QUERY_XPATH_POS_INDEX

          static final java.lang.String QUERY_XPATH_POS_INDEX

      The presence of this key indicates that the index position notation for same-name siblings is supported within XPath queries.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### QUERY_XPATH_DOC_ORDER

          static final java.lang.String QUERY_XPATH_DOC_ORDER

      The presence of this key indicates that XPath queries return results in document order.
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getDescriptorKeys

          java.lang.String[] getDescriptorKeys()

      Returns a string array holding all descriptor keys available for this implementation. This set must contain at least the built-in keys defined by the string constants in this interface.Used in conjunction with `getDescriptor(String name)` to query information about this repository implementation.

    <!-- -->

    - #### getDescriptor

          java.lang.String getDescriptor(java.lang.String key)

      Returns the descriptor for the specified key. Used to query information about this repository implementation. The set of available keys can be found by calling `getDescriptorKeys()`. If the specifed key is not found, `null` is returned.
      Parameters:
      `key` - a string corresponding to a descriptor for this repository implementation.

      Returns:
      a descriptor string

    <!-- -->

    - #### login

          Session login(Credentials credentials,
                        java.lang.String workspaceName)
                 throws LoginException,
                        NoSuchWorkspaceException,
                        RepositoryException

      Authenticates the user using the supplied `credentials`.
      If `workspaceName` is recognized as the name of an existing workspace in the repository and authorization to access that workspace is granted, then a new `Session` object is returned. The format of the string `workspaceName` depends upon the implementation.

      If `credentials` is `null`, it is assumed that authentication is handled by a mechanism external to the repository itself (for example, through the JAAS framework) and that the repository implementation exists within a context (for example, an application server) that allows it to handle authorization of the request for access to the specified workspace.

      If `workspaceName` is `null`, a default workspace is automatically selected by the repository implementation. This may, for example, be the "home workspace" of the user whose credentials were passed, though this is entirely up to the configuration and implementation of the repository. Alternatively, it may be a "null workspace" that serves only to provide the method [`Workspace.getAccessibleWorkspaceNames()`](Workspace.md), allowing the client to select from among available "real" workspaces.

      If authentication or authorization for the specified workspace fails, a `LoginException` is thrown.

      If `workspaceName` is not recognized, a `NoSuchWorkspaceException` is thrown.

      Parameters:
      `credentials` - The credentials of the user

      `workspaceName` - the name of a workspace.

      Returns:
      a valid session for the user to access the repository.

      Throws:
      [`LoginException`](LoginException.md) - If the login fails.

      [`NoSuchWorkspaceException`](NoSuchWorkspaceException.md) - If the specified `workspaceName` is not recognized.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### login

          Session login(Credentials credentials)
                 throws LoginException,
                        RepositoryException

      Equivalent to `login(credentials, null)`.
      Parameters:
      `credentials` - The credentials of the user

      Returns:
      a valid session for the user to access the repository.

      Throws:
      [`LoginException`](LoginException.md) - If the login authentication fails.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### login

          Session login(java.lang.String workspaceName)
                 throws LoginException,
                        NoSuchWorkspaceException,
                        RepositoryException

      Equivalent to `login(null, workspaceName)`.
      Parameters:
      `workspaceName` - the name of a workspace.

      Returns:
      a valid session for the user to access the repository.

      Throws:
      [`LoginException`](LoginException.md) - If the login authentication fails.

      [`NoSuchWorkspaceException`](NoSuchWorkspaceException.md) - If the specified `workspaceName` is not recognized.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### login

          Session login()
                 throws LoginException,
                        RepositoryException

      Equivalent to `login(null, null)`.
      Returns:
      a valid session for the user to access the repository.

      Throws:
      [`LoginException`](LoginException.md) - If the login authentication fails.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

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

- **[Prev Class](ReferentialIntegrityException.md)**
- **[Next Class](RepositoryException.md)**

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

**Copyright © 2004-2005 Day Software Management AG. All Rights Reserved.**
