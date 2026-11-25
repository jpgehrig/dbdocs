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

- [Prev Class](AQjmsTextMessage.md)
- [Next Class](AQjmsTopicConnectionFactory.md)

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

## Class AQjmsTopicBrowser

- java.lang.Object

- - oracle.jms.AQjmsObject

  - - oracle.jms.AQjmsTopicBrowser

<!-- -->

- All Implemented Interfaces:
  java.util.Enumeration, [TopicBrowser](TopicBrowser.md)

  ------------------------------------------------------------------------



      public class AQjmsTopicBrowser
      extends oracle.jms.AQjmsObject
      implements TopicBrowser, java.util.Enumeration

  This is an Oracle class which implements `javax.jms.TopicBrowser` and `java.util.Enumeration`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                                   |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
    | `void`                              | `close``()`<br>Public for test harness purposes                                                                          |
    | `java.util.Enumeration`             | `getEnumeration``()`<br>Gets an enumeration for browsing the current topic messages in the order they would be received. |
    | `java.lang.String`                  | `getMessageSelector``()`<br>Gets this topic browser's message selector expression.                                       |
    | [`Topic`](../../javax/jms/Topic.md) | `getTopic``()`<br>Gets the topic associated with this topic browser.                                                     |
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
      [`close`](TopicBrowser.md) in interface [`TopicBrowser`](TopicBrowser.md)

      Overrides:
      `close` in class `oracle.jms.AQjmsObject`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a JMS fails to close this Browser due to some JMS error.

    <!-- -->

    - #### getTopic

          public Topic getTopic()
                         throws JMSException

      Gets the topic associated with this topic browser.
      Specified by:
      [`getTopic`](TopicBrowser.md) in interface [`TopicBrowser`](TopicBrowser.md)

      Returns:
      the topic

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the topic is not retrieved due to some error.

    <!-- -->

    - #### getEnumeration

          public java.util.Enumeration getEnumeration()

      Gets an enumeration for browsing the current topic messages in the order they would be received.
      If `getEnumeration()` is called twice on the same TopicBrowser, the same enumeration object is returned both times. Hence calling `nextElement()` on one enumeration object would modify the state of both enumeration objects.

      Specified by:
      [`getEnumeration`](TopicBrowser.md) in interface [`TopicBrowser`](TopicBrowser.md)

      Returns:
      an enumeration for browsing the messages

    <!-- -->

    - #### getMessageSelector

          public java.lang.String getMessageSelector()
                                              throws JMSException

      Gets this topic browser's message selector expression.
      Specified by:
      [`getMessageSelector`](TopicBrowser.md) in interface [`TopicBrowser`](TopicBrowser.md)

      Returns:
      this topic browser's message selector

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message selector is not retrieved due to some error.

    <!-- -->

    - #### nextElement

          public java.lang.Object nextElement()
                                       throws java.util.NoSuchElementException

      Returns the next element of this enumeration.
      Attempts to use cached messages (if one is available from a previous call to `hasMoreElements()`). If the browser's selector used message ID, only one message can ever be returned during the browse; caches this state for subsequent calls.

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
      Attempts to cach messages (for use by a subsequent call to `nextElement()`). If the browser's selector uses message ID, only one message can ever be returned during the browse; caches this state for subsequent calls.

      Specified by:
      `hasMoreElements` in interface `java.util.Enumeration`

      Returns:
      `true` if more elements exist in the enumeration, `false` otherwise

    <!-- -->

    - #### purgeSeen

          public void purgeSeen()
                         throws JMSException

      Purges messages seen so far during browse. The purge will be finalized only when the session for the topic browse is committed.
      Specified by:
      [`purgeSeen`](TopicBrowser.md) in interface [`TopicBrowser`](TopicBrowser.md)

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

- [Prev Class](AQjmsTextMessage.md)
- [Next Class](AQjmsTopicConnectionFactory.md)

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
