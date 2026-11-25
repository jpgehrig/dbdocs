Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](Destination.md)
- [Next Class](IllegalStateException.md)

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

javax.jms

## Interface ExceptionListener

-

  ------------------------------------------------------------------------



      public interface ExceptionListener

  If a JMS provider detects a serious problem with a `Connection` object, it informs the `Connection` object's `ExceptionListener`, if one has been registered. It does this by calling the listener's `onException` method, passing it a `JMSException` argument describing the problem.
  An exception listener allows a client to be notified of a problem asynchronously. Some connections only consume messages, so they would have no other way to learn that their connection has failed.

  A JMS provider should attempt to resolve connection problems itself before it notifies the client of them.

  See Also:
  [`Connection.setExceptionListener(ExceptionListener)`](Connection.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                              |
    |-------------------|-----------------------------------------------------------------------------------------------------|
    | `void`            | `onException``(`[`JMSException`](JMSException.md)` exception)`<br>Notifies user of a JMS exception. |

<!-- -->

- - ### Method Detail

    - #### onException

          void onException(JMSException exception)

      Notifies user of a JMS exception.
      Parameters:
      `exception` - the JMS exception

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](Destination.md)
- [Next Class](IllegalStateException.md)

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

Copyright © 2001, 2019, Oracle and/or its affiliates. All rights reserved.
