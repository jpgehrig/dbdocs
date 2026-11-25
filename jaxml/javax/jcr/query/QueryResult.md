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

- **[Prev Class](QueryManager.md)**
- **[Next Class](Row.md)**

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

## **Interface QueryResult**

- **All Known Subinterfaces:**
  **[OracleQueryResult](../../../oracle/jcr/query/OracleQueryResult.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface QueryResult

  **A QueryResult object. Returned by [`Query.execute()`](Query.md).**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                    | Method and Description                                                                                |
    |--------------------------------------|-------------------------------------------------------------------------------------------------------|
    | `java.lang.String[]`                 | `getColumnNames``()`<br>Returns an array of all the property names (column names) in this result set. |
    | [`NodeIterator`](../NodeIterator.md) | `getNodes``()`<br>Returns an iterator over all nodes that match the query.                            |
    | [`RowIterator`](RowIterator.md)      | `getRows``()`<br>Returns an iterator over the `Row`s of the query result table.                       |

<!-- -->

- - ### Method Detail

    - #### getColumnNames

          java.lang.String[] getColumnNames()
                                     throws RepositoryException

      Returns an array of all the property names (column names) in this result set.
      Returns:
      a `PropertyIterator`

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getRows

          RowIterator getRows()
                       throws RepositoryException

      Returns an iterator over the `Row`s of the query result table. If an `ORDER BY` clause was specified in the query, then the order of the returned properties in the iterator will reflect the order specified in that clause. If no items match, an empty iterator is returned.
      Returns:
      a `RowIterator`

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getNodes

          NodeIterator getNodes()
                         throws RepositoryException

      Returns an iterator over all nodes that match the query. If an `ORDER BY` clause was specified in the query, then the order of the returned nodes in the iterator will reflect the order specified in that clause. If no nodes match, an empty iterator is returned.
      Returns:
      a `NodeIterator`

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

- **[Prev Class](QueryManager.md)**
- **[Next Class](Row.md)**

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
