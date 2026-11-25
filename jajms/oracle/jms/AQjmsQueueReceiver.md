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

- [Prev Class](AQjmsQueueConnectionFactory.md)
- [Next Class](AQjmsQueueSender.md)

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

oracle.jms

## Interface AQjmsQueueReceiver

- All Superinterfaces:
  [MessageConsumer](../../javax/jms/MessageConsumer.md), [QueueReceiver](../../javax/jms/QueueReceiver.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsConsumer](AQjmsConsumer.md)

  ------------------------------------------------------------------------



      public interface AQjmsQueueReceiver
      extends QueueReceiver

  Adds Oracle® Database Advanced Queuing extensions to `javax.jms.QueueReceiver`.
  Allows use of transformations and AQ navigation modes

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                          |
    |--------------------|-------------------------------------------------------------------------------------------------|
    | `int`              | `getNavigationMode``()`<br>get the navigation mode used for receiving messagess                 |
    | `java.lang.String` | `getTransformation``()`<br>Get the transformation for the `QueueReceiver`                       |
    | `void`             | `receiveNoData``()`<br>Consume the message without returning it to the user.                    |
    | `void`             | `receiveNoData``(long timeout)`<br>Consume the message without returning it to the user.        |
    | `void`             | `setNavigationMode``(int mode)`<br>set the navigation mode used for receiving messagess         |
    | `void`             | `setTransformation``(java.lang.String transformation)`<br>Set transformation for this receiver. |

    - ### Methods inherited from interface javax.jms.[QueueReceiver](../../javax/jms/QueueReceiver.md)

      [`getQueue`](../../javax/jms/QueueReceiver.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[MessageConsumer](../../javax/jms/MessageConsumer.md)

      [`close`](../../javax/jms/MessageConsumer.md)`, `[`getMessageListener`](../../javax/jms/MessageConsumer.md)`, `[`getMessageSelector`](../../javax/jms/MessageConsumer.md)`, `[`receive`](../../javax/jms/MessageConsumer.md)`, `[`receive`](../../javax/jms/MessageConsumer.md)`, `[`receiveNoWait`](../../javax/jms/MessageConsumer.md)`, `[`setMessageListener`](../../javax/jms/MessageConsumer.md)

<!-- -->

- - ### Method Detail

    - #### getNavigationMode

          int getNavigationMode()
                         throws JMSException

      get the navigation mode used for receiving messagess
      Returns:
      the navigation mode. See the "Oracle® Database Advanced Queuing User's Guide and Reference" for the explanation of the navigation mode.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if there was an error in getting the navigation mode

    <!-- -->

    - #### setNavigationMode

          void setNavigationMode(int mode)
                          throws JMSException

      set the navigation mode used for receiving messagess
      Parameters:
      `mode` - the new value of the navigation mode. See the "Oracle® Database Advanced Queuing User's Guide and Reference" for explanation of the navigation mode. The valid values of this parameter are oracle.jms.AQjmsConstants.NAVIGATION_FIRST_MESSAGE oracle.jms.AQjmsConstants.NAVIGATION_NEXT_MESSAGE oracle.jms.AQjmsConstants.NAVIGATION_NEXT_TRANSACTION

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if there was an error in setting the navigation mode

    <!-- -->

    - #### receiveNoData

          void receiveNoData()
                      throws JMSException

      Consume the message without returning it to the user. This call will avoid the ovehead of fetching the message from the database and hence can be used as an optimization by jms clients who have already got the message for example using a queue browser. This call will block until a message arrives.
      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message could not be received due to an error

    <!-- -->

    - #### receiveNoData

          void receiveNoData(long timeout)
                      throws JMSException

      Consume the message without returning it to the user. This call will avoid the ovehead of fetching the message from the database and hence can be used as an optimization by jms clients who have already got the message for example using a queue browser. This call will block until a message arrives or the timeout expires
      Parameters:
      `timeout` - the timeout value in milliseconds

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message could not be received due to an error

    <!-- -->

    - #### setTransformation

          void setTransformation(java.lang.String transformation)

      Set transformation for this receiver. This transformation will be applied before the message is returned to the user.
      Parameters:
      `transformation` - transformation name

    <!-- -->

    - #### getTransformation

          java.lang.String getTransformation()

      Get the transformation for the `QueueReceiver`

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

- [Prev Class](AQjmsQueueConnectionFactory.md)
- [Next Class](AQjmsQueueSender.md)

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
