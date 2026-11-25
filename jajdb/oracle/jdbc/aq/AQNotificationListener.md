Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQNotificationListener.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQNotificationEvent.EventType.md)
- [Next Class](AQNotificationRegistration.md)

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

oracle.jdbc.aq

## Interface AQNotificationListener

- All Superinterfaces:
  [EventListener](http://download.oracle.com/javase/8/docs/api/java/util/EventListener.html?is-external=true)

  ------------------------------------------------------------------------



      public interface AQNotificationListener
      extends EventListener

  The listener interface for receiving AQ notification events. The class that is interested in processing an AQ notification event implements this interface, and the object created with that class is registered with an `AQNotificationRegistration`, using it's `addListener` method. When the AQ event occurs, that object's `onAQNotification` method is invoked.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `onAQNotification``(`[`AQNotificationEvent`](AQNotificationEvent.md)` e)`<br>This method will be invoked whenever an AQ event occurs. |

<!-- -->

- - ### Method Detail

    - #### onAQNotification

          void onAQNotification(AQNotificationEvent e)

      This method will be invoked whenever an AQ event occurs. Note that you can control which thread will invoke this method by specifying an executor when you register this listener. If the code inside this method is time/resource consuming, then it is recommended to use your own thread otherwise you may starve the other listeners.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQNotificationListener.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQNotificationEvent.EventType.md)
- [Next Class](AQNotificationRegistration.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
