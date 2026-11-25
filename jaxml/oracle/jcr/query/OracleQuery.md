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
- **[Next Class](OracleQueryResult.md)**

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

**oracle.jcr.query**

## **Interface OracleQuery**

- **All Superinterfaces:**
  **[Query](../../../javax/jcr/query/Query.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **OracleQuery is a parsed JCR query.**
  **
  **

      public interface OracleQuery
      extends Query

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface javax.jcr.query.[Query](../../../javax/jcr/query/Query.md)**

      **[`SQL`](../../../javax/jcr/query/Query.md)`, `[`XPATH`](../../../javax/jcr/query/Query.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                        | Method and Description                                                 |
    |----------------------------------------------------------|------------------------------------------------------------------------|
    | [`QueryResult`](../../../javax/jcr/query/QueryResult.md) | `execute``()`<br>Deprecated. <br>Equivalent to `execute(false)`.       |
    | [`OracleQueryResult`](OracleQueryResult.md)              | `execute``(boolean willClose)`<br>Deprecated. <br>Executes this query. |

    - ### Methods inherited from interface javax.jcr.query.[Query](../../../javax/jcr/query/Query.md)

      [`getLanguage`](../../../javax/jcr/query/Query.md)`, `[`getStatement`](../../../javax/jcr/query/Query.md)`, `[`getStoredQueryPath`](../../../javax/jcr/query/Query.md)`, `[`storeAsNode`](../../../javax/jcr/query/Query.md)

<!-- -->

- - ### Method Detail

    - #### execute

          QueryResult execute()
                       throws RepositoryException

      Deprecated. 
      Equivalent to `execute(false)`.
      Specified by:
      [`execute`](../../../javax/jcr/query/Query.md) in interface [`Query`](../../../javax/jcr/query/Query.md)

      Returns:
      the query results

      Throws:
      [`RepositoryException`](../../../javax/jcr/RepositoryException.md) - if the operation fails

    <!-- -->

    - #### execute

          OracleQueryResult execute(boolean willClose)
                             throws RepositoryException

      Deprecated. 
      Executes this query.
      A query can be executed in either of two modes:

      If `willClose` is `false`, the query will be executed and all results will be immediately retrieved. The `getRows` and `getNodes` methods on the returned OracleQueryResult can be called repeatedly, and the `getSize` method on the RowIterator and NodeIterator objects returned by these methods will accurately report the number of query results.

      If `willClose` is `true`, the query will be executed but the results may not be retrieved until needed. This may both improve performance and decrease memory footprint. However, this mode requires the `close` method of the returned OracleQueryResult to be called to release resources held by the query. Also, the `getRows` and `getNodes` methods of the returned OracleQueryResult may be called no more than once and calling one precludes calling the other. Finally, calling `getSize` on the RowIterator and NodeIterator objects returned by these methods may return `-1`, meaning "unknown".
      Parameters:
      `willClose` - if `true`, the caller *must* call `close` on the returned `OracleQueryResult` when finished processing query results

      Returns:
      the query results

      Throws:
      [`RepositoryException`](../../../javax/jcr/RepositoryException.md) - if the operation fails

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
- **[Next Class](OracleQueryResult.md)**

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
