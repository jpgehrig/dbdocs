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

- **[Prev Class](QueryResult.md)**
- **[Next Class](RowIterator.md)**

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

## **Interface Row**

-

  ------------------------------------------------------------------------

  **
  **

      public interface Row

  **A row in the query result table.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type          | Method and Description                                                                                                                                    |
    |----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Value`](../Value.md)     | `getValue``(java.lang.String propertyName)`<br>Returns the value of the indicated property in this `Row`.                                                 |
    | [`Value`](../Value.md)`[]` | `getValues``()`<br>Returns an array of all the values in the same order as the column names returned by [`QueryResult.getColumnNames()`](QueryResult.md). |

<!-- -->

- - ### Method Detail

    - #### getValues

          Value[] getValues()
                     throws RepositoryException

      Returns an array of all the values in the same order as the column names returned by [`QueryResult.getColumnNames()`](QueryResult.md).
      Returns:
      a `Value` array.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs

    <!-- -->

    - #### getValue

          Value getValue(java.lang.String propertyName)
                  throws ItemNotFoundException,
                         RepositoryException

      Returns the value of the indicated property in this `Row`.
      If `propertyName` is not among the column names of the query result table, an `ItemNotFoundException` is thrown.

      Returns:
      a `Value`

      Throws:
      [`ItemNotFoundException`](../ItemNotFoundException.md) - if `propertyName` s not among the column names of the query result table

      [`RepositoryException`](../RepositoryException.md) - if anopther error occurs.

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

- **[Prev Class](QueryResult.md)**
- **[Next Class](RowIterator.md)**

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
