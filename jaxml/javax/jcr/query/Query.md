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

- **[Prev Class](InvalidQueryException.md)**
- **[Next Class](QueryManager.md)**

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

**javax.jcr.query**

## **Interface Query**

- **All Known Subinterfaces:**
  **[OracleQuery](../../../oracle/jcr/query/OracleQuery.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Query

  **A `Query` object.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                           |
    |---------------------------|---------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `SQL`<br>A String constant representing the SQL query language applied to the *database view* of the workspace.                 |
    | `static java.lang.String` | `XPATH`<br>A String constant representing the XPath query language applied to the *document view* XML mapping of the workspace. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type               | Method and Description                                                                                                                                                                                                                                                                                                             |
    |---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`QueryResult`](QueryResult.md) | `execute``()`<br>Executes this query and returns a [`QueryResult`](QueryResult.md).                                                                                                                                                                                                                                                |
    | `java.lang.String`              | `getLanguage``()`<br>Returns the language set for this query.                                                                                                                                                                                                                                                                      |
    | `java.lang.String`              | `getStatement``()`<br>Returns the statement set for this query.                                                                                                                                                                                                                                                                    |
    | `java.lang.String`              | `getStoredQueryPath``()`<br>If this is a `Query` object that has been stored using `storeAsNode(java.lang.String)` (regardless of whether it has been `save`d yet) or retrieved using [`QueryManager.getQuery(javax.jcr.Node)`](QueryManager.md)), then this method returns the path of the `nt:query` node that stores the query. |
    | [`Node`](../Node.md)            | `storeAsNode``(java.lang.String absPath)`<br>Creates a node representing this `Query` in content.                                                                                                                                                                                                                                  |

<!-- -->

- - ### Field Detail

    - #### XPATH

          static final java.lang.String XPATH

      A String constant representing the XPath query language applied to the *document view* XML mapping of the workspace.
      This language must be supported in level 1 repositories.

      Used when defining a query using [`QueryManager.createQuery(java.lang.String, java.lang.String)`](QueryManager.md). Also among the strings returned by [`QueryManager.getSupportedQueryLanguages()`](QueryManager.md).

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SQL

          static final java.lang.String SQL

      A String constant representing the SQL query language applied to the *database view* of the workspace.
      This language is optional.

      Used when defining a query using [`QueryManager.createQuery(java.lang.String, java.lang.String)`](QueryManager.md). Also among the strings returned by [`QueryManager.getSupportedQueryLanguages()`](QueryManager.md).

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### execute

          QueryResult execute()
                       throws RepositoryException

      Executes this query and returns a [`QueryResult`](QueryResult.md).
      Returns:
      a `QueryResult`

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs

    <!-- -->

    - #### getStatement

          java.lang.String getStatement()

      Returns the statement set for this query.
      Returns:
      the query statement.

    <!-- -->

    - #### getLanguage

          java.lang.String getLanguage()

      Returns the language set for this query. This will be one of the query language constants returned by [`QueryManager.getSupportedQueryLanguages()`](QueryManager.md).
      Returns:
      the query language.

    <!-- -->

    - #### getStoredQueryPath

          java.lang.String getStoredQueryPath()
                                       throws ItemNotFoundException,
                                              RepositoryException

      If this is a `Query` object that has been stored using `storeAsNode(java.lang.String)` (regardless of whether it has been `save`d yet) or retrieved using [`QueryManager.getQuery(javax.jcr.Node)`](QueryManager.md)), then this method returns the path of the `nt:query` node that stores the query. If this is a transient query (that is, a `Query` object created with [`QueryManager.createQuery(java.lang.String, java.lang.String)`](QueryManager.md) but not yet stored) then this method throws an `ItemNotFoundException`.
      Returns:
      path of the node representing this query.

      Throws:
      [`ItemNotFoundException`](../ItemNotFoundException.md) - if this query is not a stored query.

      [`RepositoryException`](../RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### storeAsNode

          Node storeAsNode(java.lang.String absPath)
                    throws ItemExistsException,
                           PathNotFoundException,
                           VersionException,
                           ConstraintViolationException,
                           LockException,
                           UnsupportedRepositoryOperationException,
                           RepositoryException

      Creates a node representing this `Query` in content.
      In a level 1 repository this method throws an `UnsupportedRepositoryOperationException`.

      In a level 2 repository it creates a node of type `nt:query` at `absPath` and returns that node.

      In order to persist the newly created node, a `save` must be performed that includes *the parent* of this new node within its scope. In other words, either a `Session.save` or an `Item.save` on the parent or higher-degree ancestor of `absPath` must be performed.

      An `ItemExistsException` will be thrown either immediately (by this method), or on `save`, if an item at the specified path already exists and same-name siblings are not allowed. Implementations may differ on when this validation is performed.

      A `PathNotFoundException` will be thrown either immediately , or on `save`, if the specified path implies intermediary nodes that do not exist. Implementations may differ on when this validation is performed.

      A `ConstraintViolationException`will be thrown either immediately or on `save`, if adding the node would violate a node type or implementation-specific constraintor if an attempt is made to add a node as the child of a property. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately (by this method), or on `save`, if the node to which the new child is being added is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately (by this method), or on `save`, if a lock prevents the addition of the node. Implementations may differ on when this validation is performed.

      Returns:
      the newly created node.

      Throws:
      [`ItemExistsException`](../ItemExistsException.md) - if an item at the specified path already exists, same-name siblings are not allowed and this implementation performs this validation immediately instead of waiting until `save`.

      [`PathNotFoundException`](../PathNotFoundException.md) - if the specified path implies intermediary `Node`s that do not exist or the last element of `relPath` has an index, and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](../nodetype/ConstraintViolationException.md) - if a node type or implementation-specific constraint is violated or if an attempt is made to add a node as the child of a property and this implementation performs this validation immediately instead of waiting until `save`.

      [`VersionException`](../version/VersionException.md) - if the node to which the new child is being added is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](../lock/LockException.md) - if a lock prevents the addition of the node and this implementation performs this validation immediately instead of waiting until `save`.

      [`UnsupportedRepositoryOperationException`](../UnsupportedRepositoryOperationException.md) - in a level 1 implementation.

      [`RepositoryException`](../RepositoryException.md) - if another error occurs or if the `relPath` provided has an index on its final element.

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

- **[Prev Class](InvalidQueryException.md)**
- **[Next Class](QueryManager.md)**

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

**Copyright © 2004-2005 Day Software Management AG. All Rights Reserved.**
