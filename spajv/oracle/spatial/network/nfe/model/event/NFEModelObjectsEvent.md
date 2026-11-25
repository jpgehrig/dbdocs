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

- [Prev Class](NFEModelObjectPropertyChangedEvent.md)
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

oracle.spatial.network.nfe.model.event

## Class NFEModelObjectsEvent

- java.lang.Object

- - java.util.EventObject

  - - [oracle.spatial.network.nfe.model.event.NFEModelEvent](NFEModelEvent.md)

    - - oracle.spatial.network.nfe.model.event.NFEModelObjectsEvent

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class NFEModelObjectsEvent
      extends NFEModelEvent

  An event where one or more model objects are involved
  See Also:
  [Serialized Form](../../../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                 |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEModelObjectsEvent``(java.lang.Object source, java.util.Collection<T> modelObjects, java.lang.Class<T> modelObjectsClass)`<br>Allocates a new model objects event object |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                  | Method and Description                                                    |
    |----------------------------------------------------|---------------------------------------------------------------------------|
    | `java.util.Collection<? extends java.lang.Object>` | `getModelObjects``()`<br>Gets all the model objects involved in the event |
    | `java.lang.Class<? extends java.lang.Object>`      | `getModelObjectsClass``()`<br>Gets the class of the model objects         |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.event.[NFEModelEvent](NFEModelEvent.md)

      [`getThreadId`](NFEModelEvent.md)`, `[`getTimestamp`](NFEModelEvent.md)`, `[`setThreadId`](NFEModelEvent.md)`, `[`setTimestamp`](NFEModelEvent.md)

    <!-- -->

    - ### Methods inherited from class java.util.EventObject

      `getSource, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEModelObjectsEvent

          public NFEModelObjectsEvent(java.lang.Object source,
                                      java.util.Collection<T> modelObjects,
                                      java.lang.Class<T> modelObjectsClass)

      Allocates a new model objects event object
      Parameters:
      `source` - where the event was fired

      `modelObjects` - a collection of model objects related to the event

      `modelObjectsClass` - the class of the event's model objects

  <!-- -->

  - ### Method Detail

    - #### getModelObjects

          public java.util.Collection<? extends java.lang.Object> getModelObjects()

      Gets all the model objects involved in the event
      Returns:
      a collection of model objects

    <!-- -->

    - #### getModelObjectsClass

          public java.lang.Class<? extends java.lang.Object> getModelObjectsClass()

      Gets the class of the model objects
      Returns:
      the model objects' Java class

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

- [Prev Class](NFEModelObjectPropertyChangedEvent.md)
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
