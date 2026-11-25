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

- [Prev Class](NFEBasicEventDispatcher.md)
- [Next Class](NFEEventDispatchException.md)

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

## Interface NFEEventDispatcher\<U extends java.util.EventListener\>

- Type Parameters:
  `U` - The type of EventListener subclass

  <!-- -->

  All Known Implementing Classes:
  [NFEBasicEventDispatcher](NFEBasicEventDispatcher.md)

  ------------------------------------------------------------------------



      public interface NFEEventDispatcher<U extends java.util.EventListener>

  Defines a utility component used for firing events

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                       |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `dispatch``(`[`NFEModelEvent`](NFEModelEvent.md)` event, java.util.Collection<U> listeners, java.lang.String listenerMethodName)`<br>Notifies about an event to a collection of listeners by invoking the given method name. |
    | `boolean`         | `isStopDispatchingAtFirstError``()`<br>Tells whether the dispatcher stops firing events when an error ocurrs                                                                                                                 |
    | `void`            | `setStopDispatchingAtFirstError``(boolean stopDispatchingAtFirstError)`<br>Sets the dispatcher to stop firing events if there is an error.                                                                                   |

<!-- -->

- - ### Method Detail

    - #### dispatch

          void dispatch(NFEModelEvent event,
                        java.util.Collection<U> listeners,
                        java.lang.String listenerMethodName)
                 throws NFEEventDispatchException

      Notifies about an event to a collection of listeners by invoking the given method name.
      Parameters:
      `event` - an NFEModelEvent (or subclass) instance

      `listeners` - a collection of listeners to be notified

      `listenerMethodName` - the method name to be invoked on the listeners

      Throws:
      [`NFEEventDispatchException`](NFEEventDispatchException.md)

    <!-- -->

    - #### setStopDispatchingAtFirstError

          void setStopDispatchingAtFirstError(boolean stopDispatchingAtFirstError)

      Sets the dispatcher to stop firing events if there is an error. Otherwise, the dispatcher should fire any events as possible and throw the exception at the end
      Parameters:
      `stopDispatchingAtFirstError` -

    <!-- -->

    - #### isStopDispatchingAtFirstError

          boolean isStopDispatchingAtFirstError()

      Tells whether the dispatcher stops firing events when an error ocurrs
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

- [Prev Class](NFEBasicEventDispatcher.md)
- [Next Class](NFEEventDispatchException.md)

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
