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

- [Prev Class](NFEEventSupport.md)
- [Next Class](NFEModelListener.md)

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

## Class NFEModelEvent

- java.lang.Object

- - java.util.EventObject

  - - oracle.spatial.network.nfe.model.event.NFEModelEvent

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  <!-- -->

  Direct Known Subclasses:
  [NFEModelObjectEvent](NFEModelObjectEvent.md), [NFEModelObjectsEvent](NFEModelObjectsEvent.md)

  ------------------------------------------------------------------------



      public class NFEModelEvent
      extends java.util.EventObject

  Root class of the Model Event hierarchy. It contains the information common to all the type of events of an NFEModel.
  See Also:
  [Serialized Form](../../../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                      |
    |----------------------------------------------------------------------------------|
    | `NFEModelEvent``(java.lang.Object source)`<br>Allocates a new model event object |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                |
    |-------------------|---------------------------------------------------------------------------------------|
    | `long`            | `getThreadId``()`<br>Gets the id of the thread where the event was fired              |
    | `long`            | `getTimestamp``()`<br>Gets the time when the event was fired                          |
    | `void`            | `setThreadId``(long threadId)`<br>Sets the id of the thread where the event was fired |
    | `void`            | `setTimestamp``(long timestamp)`<br>Sets the time when the event was fired            |

    - ### Methods inherited from class java.util.EventObject

      `getSource, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEModelEvent

          public NFEModelEvent(java.lang.Object source)

      Allocates a new model event object
      Parameters:
      `source` - Where the event was fired

  <!-- -->

  - ### Method Detail

    - #### getThreadId

          public long getThreadId()

      Gets the id of the thread where the event was fired
      Returns:

    <!-- -->

    - #### setThreadId

          public void setThreadId(long threadId)

      Sets the id of the thread where the event was fired
      Parameters:
      `threadId` - a thread id

    <!-- -->

    - #### getTimestamp

          public long getTimestamp()

      Gets the time when the event was fired
      Returns:
      a time stamp

    <!-- -->

    - #### setTimestamp

          public void setTimestamp(long timestamp)

      Sets the time when the event was fired
      Parameters:
      `timestamp` - a time stamp

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

- [Prev Class](NFEEventSupport.md)
- [Next Class](NFEModelListener.md)

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
