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

- [Prev Class](NFEModelObjectEvent.md)
- [Next Class](NFEModelObjectsEvent.md)

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

## Class NFEModelObjectPropertyChangedEvent

- java.lang.Object

- - java.util.EventObject

  - - [oracle.spatial.network.nfe.model.event.NFEModelEvent](NFEModelEvent.md)

    - - [oracle.spatial.network.nfe.model.event.NFEModelObjectEvent](NFEModelObjectEvent.md)

      - - oracle.spatial.network.nfe.model.event.NFEModelObjectPropertyChangedEvent

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class NFEModelObjectPropertyChangedEvent
      extends NFEModelObjectEvent

  Event that contains information regarding to a changed property of a model object.
  See Also:
  [Serialized Form](../../../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEModelObjectPropertyChangedEvent``(java.lang.Object source, java.lang.Object modelObject, java.lang.String propertyName, java.lang.Object previousPropertyValue)`<br>Allocates a new model object property change event |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                         |
    |--------------------|--------------------------------------------------------------------------------|
    | `java.lang.Object` | `getPreviousValue``()`<br>Gets the value of the property before it was changed |
    | `java.lang.String` | `getPropertyName``()`<br>Gets the name of the changed property                 |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.event.[NFEModelObjectEvent](NFEModelObjectEvent.md)

      [`getModelObject`](NFEModelObjectEvent.md)

    <!-- -->

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

    - #### NFEModelObjectPropertyChangedEvent

          public NFEModelObjectPropertyChangedEvent(java.lang.Object source,
                                                    java.lang.Object modelObject,
                                                    java.lang.String propertyName,
                                                    java.lang.Object previousPropertyValue)

      Allocates a new model object property change event
      Parameters:
      `source` - where the event was fired

      `modelObject` - the model object related to the event

      `propertyName` - the name of the changed property

      `previousPropertyValue` - the value of the property before the change

  <!-- -->

  - ### Method Detail

    - #### getPropertyName

          public java.lang.String getPropertyName()

      Gets the name of the changed property
      Returns:
      a property name

    <!-- -->

    - #### getPreviousValue

          public java.lang.Object getPreviousValue()

      Gets the value of the property before it was changed
      Returns:
      the old property value

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

- [Prev Class](NFEModelObjectEvent.md)
- [Next Class](NFEModelObjectsEvent.md)

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
