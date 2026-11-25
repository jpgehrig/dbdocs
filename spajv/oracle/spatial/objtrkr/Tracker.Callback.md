Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](Tracker.md)
- [Next Class](Tracker.NotificationType.md)

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

oracle.spatial.objtrkr

## Interface Tracker.Callback\<T\>

- Type Parameters:
  `T` - the type to accept

  <!-- -->

  Enclosing class:
  [Tracker](Tracker.md)

  <!-- -->

  Functional Interface:
  This is a functional interface and can therefore be used as the assignment target for a lambda expression or method reference.

  ------------------------------------------------------------------------



      @FunctionalInterface
      public static interface Tracker.Callback<T>

  Equivalent to consumer lambda, but allows SQLException and JMSException.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description |
    |-------------------|------------------------|
    | `void`            | `accept``(T msg)`      |

<!-- -->

- - ### Method Detail

    - #### accept

          void accept(T msg)
               throws java.sql.SQLException,
                      JMSException

      Throws:
      `java.sql.SQLException`

      `JMSException`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](Tracker.md)
- [Next Class](Tracker.NotificationType.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
