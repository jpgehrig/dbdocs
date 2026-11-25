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

- **[Prev Class](OracleQuery.md)**
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

**oracle.jcr.query**

## **Interface OracleQueryResult**

- **All Superinterfaces:**
  **[QueryResult](../../../javax/jcr/query/QueryResult.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **OracleQueryResult is the result of executing an OracleQuery.**
  **
  **

      public interface OracleQueryResult
      extends QueryResult

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type | Method and Description                                                                      |
    |-------------------|---------------------------------------------------------------------------------------------|
    | `void`            | `close``()`<br>Deprecated. <br>Closes this OracleQueryResult, releasing any resources held. |

    - ### Methods inherited from interface javax.jcr.query.[QueryResult](../../../javax/jcr/query/QueryResult.md)

      [`getColumnNames`](../../../javax/jcr/query/QueryResult.md)`, `[`getNodes`](../../../javax/jcr/query/QueryResult.md)`, `[`getRows`](../../../javax/jcr/query/QueryResult.md)

<!-- -->

- - ### Method Detail

    - #### close

          void close()

      Deprecated. 
      Closes this OracleQueryResult, releasing any resources held.
      If this OracleQueryResult was returned by calling the `execute` method of OracleQuery with a `willClose` of `true`, `close` *must* be called after processing query results to ensure all resources held by the query are released.

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

- **[Prev Class](OracleQuery.md)**
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
