Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- [Prev Class](NodeDownEvent.md)
- [Next Class](ServiceDownEvent.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.simplefan

## Class NodeUpEvent

- java.lang.Object

- - java.util.EventObject

  - - [oracle.simplefan.FanEvent](FanEvent.md)

    - - oracle.simplefan.NodeUpEvent

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Cloneable

  ------------------------------------------------------------------------



      public abstract class NodeUpEvent
      extends FanEvent
      implements java.lang.Cloneable, java.io.Serializable

  The event posted when a node gets UP.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                         |
    |---------------------------------------------------------------------|
    | `NodeUpEvent``(java.lang.Object source, java.util.Date timestamp)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type           | Method and Description |
    |-----------------------------|------------------------|
    | `abstract int`              | `getIncarnation``()`   |
    | `abstract java.lang.String` | `getNodeName``()`      |

    - ### Methods inherited from class oracle.simplefan.[FanEvent](FanEvent.md)

      [`getTimestamp`](FanEvent.md)

    <!-- -->

    - ### Methods inherited from class java.util.EventObject

      `getSource, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NodeUpEvent

          public NodeUpEvent(java.lang.Object source,
                             java.util.Date timestamp)

  <!-- -->

  - ### Method Detail

    - #### getNodeName

          public abstract java.lang.String getNodeName()

    <!-- -->

    - #### getIncarnation

          public abstract int getIncarnation()

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- [Prev Class](NodeDownEvent.md)
- [Next Class](ServiceDownEvent.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2008, 2019, Oracle and/or its affiliates. All rights reserved.
