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

- [Prev Class](NFEEventDispatchException.md)
- [Next Class](NFEModelEvent.md)

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

oracle.spatial.network.nfe.model.event

## Class NFEEventSupport\<U extends java.util.EventListener\>

- java.lang.Object

- - oracle.spatial.network.nfe.model.event.NFEEventSupport\<U\>

<!-- -->

- Type Parameters:
  `U` - The type of EventListener subclass

  ------------------------------------------------------------------------



      public class NFEEventSupport<U extends java.util.EventListener>
      extends java.lang.Object

  Utility class used to subscribe and remove listener used by class which fire model events.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                     |
    |-----------------------------------------------------------------|
    | `NFEEventSupport``()`<br>Allocates a new NFEEventSupport object |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type         | Method and Description                               |
    |---------------------------|------------------------------------------------------|
    | `void`                    | `addListener``(U listener)`<br>Adds a new listener   |
    | `java.util.Collection<U>` | `getListeners``()`<br>Gets all the listeners         |
    | `void`                    | `removeListener``(U listener)`<br>Removes a listener |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEEventSupport

          public NFEEventSupport()

      Allocates a new NFEEventSupport object

  <!-- -->

  - ### Method Detail

    - #### addListener

          public void addListener(U listener)

      Adds a new listener
      Parameters:
      `listener` - listener

    <!-- -->

    - #### removeListener

          public void removeListener(U listener)

      Removes a listener
      Parameters:
      `listener` -

    <!-- -->

    - #### getListeners

          public java.util.Collection<U> getListeners()

      Gets all the listeners
      Returns:
      listeners

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

- [Prev Class](NFEEventDispatchException.md)
- [Next Class](NFEModelEvent.md)

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
