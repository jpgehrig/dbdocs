Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEConnectionDataSource.md)
- Next Class

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.spatial.network.nfe.io.jdbc

## Class SQLValidator

- java.lang.Object

- - oracle.spatial.network.nfe.io.jdbc.SQLValidator

<!-- -->

-

  ------------------------------------------------------------------------



      public class SQLValidator
      extends java.lang.Object

  General validator for standard sql naming conventions.

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                                                                                                                     |
    |-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static SQLValidator` | `getInstance``()`<br>Method to get an instance from SQLValidator (Singleton).                                                                                                                              |
    | `java.lang.String`    | `getValidatedQuery``(java.sql.Connection conn, java.lang.String wildCardedQuery, java.lang.String... sqlNames)`<br>Receives a wildCarded SQL query and a list of SQL Names as parameters of the wildCards. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getInstance

          public static SQLValidator getInstance()

      Method to get an instance from SQLValidator (Singleton).
      Returns:
      SQLValidator instance.

    <!-- -->

    - #### getValidatedQuery

          public java.lang.String getValidatedQuery(java.sql.Connection conn,
                                                    java.lang.String wildCardedQuery,
                                                    java.lang.String... sqlNames)
                                             throws NFEIOException

      Receives a wildCarded SQL query and a list of SQL Names as parameters of the wildCards. Validates if all the sql Names are valid ones, and if so, replaces the wildCards and returns the complete query.
      Parameters:
      `conn` - Connection to the Database

      `wildCardedQuery` - Query with the wildCards in the form of :parameter

      `sqlNames` - List of sql names

      Returns:
      the completed query with all the validates sql names

      Throws:
      [`NFEIOException`](../NFEIOException.md) - An exception listing the invalid names. Error Code: [`NFEIOException.INVALID_SQL_NAME`](../NFEIOException.md).

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEConnectionDataSource.md)
- Next Class

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
