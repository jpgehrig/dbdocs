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

- Prev Class
- [Next Class](NFEEventDispatcher.md)

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

## Class NFEBasicEventDispatcher\<U extends java.util.EventListener\>

- java.lang.Object

- - oracle.spatial.network.nfe.model.event.NFEBasicEventDispatcher\<U\>

<!-- -->

- Type Parameters:
  `U` - The type of EventListener subclass

  <!-- -->

  All Implemented Interfaces:
  [NFEEventDispatcher](NFEEventDispatcher.md)\<U\>

  ------------------------------------------------------------------------



      public class NFEBasicEventDispatcher<U extends java.util.EventListener>
      extends java.lang.Object
      implements NFEEventDispatcher<U>

  An implementation of NFEEventDispatcher that fires all the event in a single thread.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description    |
    |--------------------------------|
    | `NFEBasicEventDispatcher``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                       |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `dispatch``(`[`NFEModelEvent`](NFEModelEvent.md)` event, java.util.Collection<U> listeners, java.lang.String listenerMethodName)`<br>Notifies about an event to a collection of listeners by invoking the given method name. |
    | `boolean`         | `isStopDispatchingAtFirstError``()`<br>Tells whether the dispatcher stops firing events when an error ocurrs                                                                                                                 |
    | `void`            | `setStopDispatchingAtFirstError``(boolean stopDispatchingAtFirstError)`<br>Sets the dispatcher to stop firing events if there is an error.                                                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicEventDispatcher

          public NFEBasicEventDispatcher()

  <!-- -->

  - ### Method Detail

    - #### dispatch

          public void dispatch(NFEModelEvent event,
                               java.util.Collection<U> listeners,
                               java.lang.String listenerMethodName)
                        throws NFEEventDispatchException

      Description copied from interface: [`NFEEventDispatcher`](NFEEventDispatcher.md)
      Notifies about an event to a collection of listeners by invoking the given method name.
      Specified by:
      [`dispatch`](NFEEventDispatcher.md) in interface [`NFEEventDispatcher`](NFEEventDispatcher.md)`<U extends java.util.EventListener>`

      Parameters:
      `event` - an NFEModelEvent (or subclass) instance

      `listeners` - a collection of listeners to be notified

      `listenerMethodName` - the method name to be invoked on the listeners

      Throws:
      [`NFEEventDispatchException`](NFEEventDispatchException.md)

    <!-- -->

    - #### setStopDispatchingAtFirstError

          public void setStopDispatchingAtFirstError(boolean stopDispatchingAtFirstError)

      Description copied from interface: [`NFEEventDispatcher`](NFEEventDispatcher.md)
      Sets the dispatcher to stop firing events if there is an error. Otherwise, the dispatcher should fire any events as possible and throw the exception at the end
      Specified by:
      [`setStopDispatchingAtFirstError`](NFEEventDispatcher.md) in interface [`NFEEventDispatcher`](NFEEventDispatcher.md)`<U extends java.util.EventListener>`

    <!-- -->

    - #### isStopDispatchingAtFirstError

          public boolean isStopDispatchingAtFirstError()

      Description copied from interface: [`NFEEventDispatcher`](NFEEventDispatcher.md)
      Tells whether the dispatcher stops firing events when an error ocurrs
      Specified by:

      [`isStopDispatchingAtFirstError`](NFEEventDispatcher.md) in interface [`NFEEventDispatcher`](NFEEventDispatcher.md)`<U extends java.util.EventListener>`

      Returns:

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

- Prev Class
- [Next Class](NFEEventDispatcher.md)

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
