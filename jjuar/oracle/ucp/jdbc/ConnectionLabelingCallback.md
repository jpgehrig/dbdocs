Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionLabelingCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionInitializationCallback.md)
- [Next Class](ConnectionWithAbandonedTimeout.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.ucp.jdbc

## Interface ConnectionLabelingCallback

- All Superinterfaces:
  [ConnectionLabelingCallback](../ConnectionLabelingCallback.md)

  ------------------------------------------------------------------------



      public interface ConnectionLabelingCallback
      extends ConnectionLabelingCallback

  New callback interface for connection labeling support. Applications using the connection labeling feature must either provide an implementation of this interface, or the one in the oracle.ucp package.
  The additional method `getRequestedLabels`in this new interface allows applications to use connection labeling with standard JDBC `getConnection` APIs. Applications do not need to specify the requested labels as part of the `getConnection` calls. Instead, the connection pool obtains the requested labels by calling this new method.

  See Also:
  [`ConnectionLabelingCallback`](../ConnectionLabelingCallback.md), [`UniversalConnectionPool`](../UniversalConnectionPool.md), [`PoolDataSource`](PoolDataSource.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type      | Method and Description                                                                                              |
    |------------------------|---------------------------------------------------------------------------------------------------------------------|
    | `java.util.Properties` | `getRequestedLabels``()`<br>Allows applications to use connection labeling with standard JDBC `getConnection` APIs. |

    - ### Methods inherited from interface oracle.ucp.[ConnectionLabelingCallback](../ConnectionLabelingCallback.md)

      [`configure`](../ConnectionLabelingCallback.md)`, `[`cost`](../ConnectionLabelingCallback.md)

<!-- -->

- - ### Method Detail

    - #### getRequestedLabels

          java.util.Properties getRequestedLabels()

      Allows applications to use connection labeling with standard JDBC `getConnection` APIs. Applications do not need to specify the requested labels as part of the `getConnection` calls.Instead, the connection pool obtains the requested labels by calling this new method.
      Returns:
      requested connection labels.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionLabelingCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionInitializationCallback.md)
- [Next Class](ConnectionWithAbandonedTimeout.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

Copyright © 2007, 2022, Oracle and/or its affiliates.
