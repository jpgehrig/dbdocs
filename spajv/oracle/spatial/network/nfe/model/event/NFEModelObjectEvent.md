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

- [Prev Class](NFEModelListener.md)
- [Next Class](NFEModelObjectPropertyChangedEvent.md)

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

## Class NFEModelObjectEvent

- java.lang.Object

- - java.util.EventObject

  - - [oracle.spatial.network.nfe.model.event.NFEModelEvent](NFEModelEvent.md)

    - - oracle.spatial.network.nfe.model.event.NFEModelObjectEvent

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  <!-- -->

  Direct Known Subclasses:
  [NFEModelObjectPropertyChangedEvent](NFEModelObjectPropertyChangedEvent.md)

  ------------------------------------------------------------------------



      public class NFEModelObjectEvent
      extends NFEModelEvent

  Represent a generic event related to an Object from the NFEModel. It can contain a model object that was added or removed. The context is provided by the listener method that receives an instance of this class as parameter.
  See Also:
  [Serialized Form](../../../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                 |
    |-----------------------------------------------------------------------------------------------------------------------------|
    | `NFEModelObjectEvent``(java.lang.Object source, java.lang.Object modelObject)`<br>Allocates a new model object event object |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                              |
    |--------------------|---------------------------------------------------------------------|
    | `java.lang.Object` | `getModelObject``()`<br>Gets the model object related to this event |

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

    - #### NFEModelObjectEvent

          public NFEModelObjectEvent(java.lang.Object source,
                                     java.lang.Object modelObject)

      Allocates a new model object event object
      Parameters:
      `source` - Where the event was fired

      `modelObject` - The object related to this event

  <!-- -->

  - ### Method Detail

    - #### getModelObject

          public java.lang.Object getModelObject()

      Gets the model object related to this event
      Returns:
      a model object. The actual type may be any of the types in an NFEModel such a feature, a feature element or a network element.

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

- [Prev Class](NFEModelListener.md)
- [Next Class](NFEModelObjectPropertyChangedEvent.md)

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
