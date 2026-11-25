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

- **[Prev Class](Query.md)**
- **[Next Class](QueryResult.md)**

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

## **Interface QueryManager**

-

  ------------------------------------------------------------------------

  **
  **

      public interface QueryManager

  **This interface encapsulates methods for the management of search queries. Provides methods for the creation and retrieval of search queries.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type    | Method and Description                                                                                                                                                                    |
    |----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Query`](Query.md)  | `createQuery``(java.lang.String statement, java.lang.String language)`<br>Creates a new query by specifying the query `statement` itself and the `language` in which the query is stated. |
    | [`Query`](Query.md)  | `getQuery``(`[`Node`](../Node.md)` node)`<br>Retrieves an existing persistent query.                                                                                                      |
    | `java.lang.String[]` | `getSupportedQueryLanguages``()`<br>Returns an array of strings representing all query languages supported by this repository.                                                            |

<!-- -->

- - ### Method Detail

    - #### createQuery

          Query createQuery(java.lang.String statement,
                            java.lang.String language)
                     throws InvalidQueryException,
                            RepositoryException

      Creates a new query by specifying the query `statement` itself and the `language` in which the query is stated. If the query `statement` is syntactically invalid, given the language specified, an `InvalidQueryException` is thrown. The `language` must be a string from among those returned by QueryManager.getSupportedQueryLanguages(); if it is not, then an `InvalidQueryException` is thrown.
      Returns:
      A `Query` object.

      Throws:
      [`InvalidQueryException`](InvalidQueryException.md) - if statement is invalid or language is unsupported.

      [`RepositoryException`](../RepositoryException.md) - if another error occurs

    <!-- -->

    - #### getQuery

          Query getQuery(Node node)
                  throws InvalidQueryException,
                         RepositoryException

      Retrieves an existing persistent query. If `node` is not a valid persisted query (that is, a node of type `nt:query`), an `InvalidQueryException` is thrown.
      Persistent queries are created by first using `QueryManager.createQuery` to create a `Query` object and then calling `Query.save` to persist the query to a location in the workspace.

      Parameters:
      `node` - a persisted query (that is, a node of type `nt:query`).

      Returns:
      a `Query` object.

      Throws:
      [`InvalidQueryException`](InvalidQueryException.md) - If `node` is not a valid persisted query (that is, a node of type `nt:query`).

      [`RepositoryException`](../RepositoryException.md) - if another error occurs

    <!-- -->

    - #### getSupportedQueryLanguages

          java.lang.String[] getSupportedQueryLanguages()
                                                 throws RepositoryException

      Returns an array of strings representing all query languages supported by this repository. In level 1 this set must include the string represented by the constant [`Query.XPATH`](Query.md). If SQL is supported it must additionally include the string represented by the constant [`Query.SQL`](Query.md). An implementation may also support other languages as well. See [`Query`](Query.md).
      Returns:
      An string array.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

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

- **[Prev Class](Query.md)**
- **[Next Class](QueryResult.md)**

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
