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

- [Prev Class](AQjmsProducer.md)
- [Next Class](AQjmsQueueConnectionFactory.md)

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

## Class AQjmsQueueBrowser

- java.lang.Object

- - oracle.jms.AQjmsObject

  - - oracle.jms.AQjmsQueueBrowser

<!-- -->

- All Implemented Interfaces:
  java.util.Enumeration, [QueueBrowser](../../javax/jms/QueueBrowser.md)

  ------------------------------------------------------------------------



      public class AQjmsQueueBrowser
      extends oracle.jms.AQjmsObject
      implements QueueBrowser, java.util.Enumeration

  This is an Oracle class which implements `javax.jms.QueueBrowser` and `java.util.Enumeration`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                                   |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
    | `void`                              | `close``()`<br>Public for test harness purposes                                                                          |
    | `java.util.Enumeration`             | `getEnumeration``()`<br>Gets an enumeration for browsing the current queue messages in the order they would be received. |
    | `java.lang.String`                  | `getMessageSelector``()`<br>Gets this queue browser's message selector expression.                                       |
    | [`Queue`](../../javax/jms/Queue.md) | `getQueue``()`<br>Gets the queue associated with this queue browser.                                                     |
    | `java.lang.String`                  | `getTransformation``()`<br>Gets this browser's transformation.                                                           |
    | `boolean`                           | `hasMoreElements``()`<br>Tests if this enumeration contains more elements.                                               |
    | `java.lang.Object`                  | `nextElement``()`<br>Returns the next element of this enumeration.                                                       |
    | `void`                              | `purgeSeen``()`<br>Purges messages seen so far during browse.                                                            |
    | `void`                              | `setTransformation``(java.lang.String transformation)`<br>Sets this browser's transformation.                            |

    - ### Methods inherited from class oracle.jms.AQjmsObject

      `checkClosed, children, finalize, getID, getParent, isOpen, localClose, preClose`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### close

          public void close()
                     throws JMSException

      Description copied from class: `oracle.jms.AQjmsObject`
      Public for test harness purposes
      Specified by:
      [`close`](../../javax/jms/QueueBrowser.md) in interface [`QueueBrowser`](../../javax/jms/QueueBrowser.md)

      Overrides:
      `close` in class `oracle.jms.AQjmsObject`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to close this browser due to some internal error.

    <!-- -->

    - #### getQueue

          public Queue getQueue()
                         throws JMSException

      Gets the queue associated with this queue browser.
      Specified by:
      [`getQueue`](../../javax/jms/QueueBrowser.md) in interface [`QueueBrowser`](../../javax/jms/QueueBrowser.md)

      Returns:
      the queue

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue is not retrieved due to some error.

    <!-- -->

    - #### getEnumeration

          public java.util.Enumeration getEnumeration()
                                               throws JMSException

      Gets an enumeration for browsing the current queue messages in the order they would be received.
      Specified by:
      [`getEnumeration`](../../javax/jms/QueueBrowser.md) in interface [`QueueBrowser`](../../javax/jms/QueueBrowser.md)

      Returns:
      an enumeration for browsing the messages

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the enumeration is not retrieved due to some error.

    <!-- -->

    - #### getMessageSelector

          public java.lang.String getMessageSelector()
                                              throws JMSException

      Gets this queue browser's message selector expression.
      Specified by:
      [`getMessageSelector`](../../javax/jms/QueueBrowser.md) in interface [`QueueBrowser`](../../javax/jms/QueueBrowser.md)

      Returns:
      this queue browser's message selector

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message selector is not retrieved due to some error.

    <!-- -->

    - #### nextElement

          public java.lang.Object nextElement()
                                       throws java.util.NoSuchElementException

      Returns the next element of this enumeration.
      Specified by:
      `nextElement` in interface `java.util.Enumeration`

      Returns:
      the next element of this enumeration

      Throws:
      `java.util.NoSuchElementException` - if no more elements exist.

    <!-- -->

    - #### hasMoreElements

          public boolean hasMoreElements()

      Tests if this enumeration contains more elements.
      Specified by:
      `hasMoreElements` in interface `java.util.Enumeration`

      Returns:
      `true` if more elements exist in the enumeration, `false` otherwise

    <!-- -->

    - #### purgeSeen

          public void purgeSeen()
                         throws JMSException

      Purges messages seen so far during browse. The purge will be finalized only when the session for the queue browse is committed.
      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an error occurs during the purge operation.

    <!-- -->

    - #### setTransformation

          public void setTransformation(java.lang.String transformation)

      Sets this browser's transformation. This transformation will be applied before the message is returned to the user.
      Parameters:
      `transformation` - the transformation to use when getting messages

    <!-- -->

    - #### getTransformation

          public java.lang.String getTransformation()

      Gets this browser's transformation.
      Returns:
      the transformation used when getting messages

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

- [Prev Class](AQjmsProducer.md)
- [Next Class](AQjmsQueueConnectionFactory.md)

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
