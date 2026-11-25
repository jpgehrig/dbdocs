Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/LogicalTransactionIdEventListener.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](LogicalTransactionIdEvent.md)
- [Next Class](NotificationRegistration.md)

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

oracle.jdbc

## Interface LogicalTransactionIdEventListener

- All Superinterfaces:
  [EventListener](http://download.oracle.com/javase/8/docs/api/java/util/EventListener.html?is-external=true)

  ------------------------------------------------------------------------



      public interface LogicalTransactionIdEventListener
      extends EventListener

  A class that is interested in processing Logical Transaction Id events must implement this interface. A listener instance is registered using one of the `OracleConnection.addLogicalTransactionIdEventListener` flavors.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                        |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `onLogicalTransactionIdEvent``(`[`LogicalTransactionIdEvent`](LogicalTransactionIdEvent.md)` event)`<br>This method is executed whenever the server sends a new Logical Transaction Id event. |

<!-- -->

- - ### Method Detail

    - #### onLogicalTransactionIdEvent

          void onLogicalTransactionIdEvent(LogicalTransactionIdEvent event)

      This method is executed whenever the server sends a new Logical Transaction Id event.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/LogicalTransactionIdEventListener.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](LogicalTransactionIdEvent.md)
- [Next Class](NotificationRegistration.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
