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

- [Prev Class](AQjmsMapMessage.md)
- [Next Class](AQjmsObjectMessage.md)

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

## Class AQjmsMessage

- java.lang.Object

- - oracle.jms.AQjmsMessage

<!-- -->

- All Implemented Interfaces:
  [Message](../../javax/jms/Message.md)

  <!-- -->

  Direct Known Subclasses:
  [AQjmsAdtMessage](AQjmsAdtMessage.md), [AQjmsBytesMessage](AQjmsBytesMessage.md), [AQjmsMapMessage](AQjmsMapMessage.md), [AQjmsObjectMessage](AQjmsObjectMessage.md), [AQjmsStreamMessage](AQjmsStreamMessage.md), [AQjmsTextMessage](AQjmsTextMessage.md)

  ------------------------------------------------------------------------



      public class AQjmsMessage
      extends java.lang.Object
      implements Message

  This is an Oracle class which implements `javax.jms.Message`.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Message](../../javax/jms/Message.md)

      [`DEFAULT_DELIVERY_MODE`](../../javax/jms/Message.md)`, `[`DEFAULT_PRIORITY`](../../javax/jms/Message.md)`, `[`DEFAULT_TIME_TO_LIVE`](../../javax/jms/Message.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                       |
    |-------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                          | `acknowledge``()`<br>Acknowleges message receipt when using the `CLIENT_ACKNOWLEDGE` mode.                                                                                   |
    | `void`                                          | `clearBody``()`<br>Clears out the message body.                                                                                                                              |
    | `void`                                          | `clearProperties``()`<br>Clears a message's properties.                                                                                                                      |
    | `int`                                           | `getAttempts``()`<br>Gets this message's retry count.                                                                                                                        |
    | `long`                                          | `getBodyLength``()`<br>Gets the number of bytes of the message body when the message is in read-only mode.                                                                   |
    | `boolean`                                       | `getBooleanProperty``(java.lang.String name)`<br>Returns a property value as a `boolean`.                                                                                    |
    | `byte`                                          | `getByteProperty``(java.lang.String name)`<br>Returns a property value as a `byte`.                                                                                          |
    | `double`                                        | `getDoubleProperty``(java.lang.String name)`<br>Returns a property value as a `double`.                                                                                      |
    | `float`                                         | `getFloatProperty``(java.lang.String name)`<br>Returns a property value as a `float`.                                                                                        |
    | `int`                                           | `getIntProperty``(java.lang.String name)`<br>Returns a property value as an `int`.                                                                                           |
    | `java.lang.String`                              | `getJMSCorrelationID``()`<br>Gets this message's correlation ID.                                                                                                             |
    | `byte[]`                                        | `getJMSCorrelationIDAsBytes``()`<br>Gets this message's correlation ID as an array of bytes.                                                                                 |
    | `int`                                           | `getJMSDeliveryMode``()`<br>Gets this message's delivery mode.                                                                                                               |
    | [`Destination`](../../javax/jms/Destination.md) | `getJMSDestination``()`<br>Gets this message's destination.                                                                                                                  |
    | `long`                                          | `getJMSExpiration``()`<br>Gets this message's expiration value.                                                                                                              |
    | `java.lang.String`                              | `getJMSMessageID``()`<br>Gets this message's ID.                                                                                                                             |
    | `byte[]`                                        | `getJMSMessageIDAsBytes``()`<br>Gets this message's ID as a byte array.                                                                                                      |
    | `int`                                           | `getJMSPriority``()`<br>Gets this message's priority.                                                                                                                        |
    | `boolean`                                       | `getJMSRedelivered``()`<br>Gets an indication of whether this message is being redelivered.                                                                                  |
    | [`Destination`](../../javax/jms/Destination.md) | `getJMSReplyTo``()`<br>Gets this message's `JMSReplyTo` destination.                                                                                                         |
    | `long`                                          | `getJMSTimestamp``()`<br>Gets this message's timestamp.                                                                                                                      |
    | `java.lang.String`                              | `getJMSType``()`<br>Gets this message's type.                                                                                                                                |
    | `long`                                          | `getLongProperty``(java.lang.String name)`<br>Returns a property value as a `long`.                                                                                          |
    | `java.lang.Object`                              | `getObjectProperty``(java.lang.String name)`<br>Returns a property value as a Java object.                                                                                   |
    | `java.util.Enumeration`                         | `getPropertyNames``()`<br>Returns an `Enumeration` of all the property names.                                                                                                |
    | `oracle.jms.AQjmsAgent`                         | `getSenderID``()`<br>Gets this message's sender ID.                                                                                                                          |
    | `short`                                         | `getShortProperty``(java.lang.String name)`<br>Returns a property value as a `short`.                                                                                        |
    | `java.lang.String`                              | `getStringProperty``(java.lang.String name)`<br>Returns a property value as a `String`.                                                                                      |
    | `java.util.Enumeration`                         | `getUserPropertyNames``()`<br>Returns an `Enumeration` of all the user property names.                                                                                       |
    | `boolean`                                       | `isLargeBody``()`<br>This method can be used by the client applications to check whether the message contains large messaege body and hence requires streaming with dequeue. |
    | `boolean`                                       | `propertyExists``(java.lang.String name)`<br>Checks if a property value exists.                                                                                              |
    | `void`                                          | `setBooleanProperty``(java.lang.String name, boolean value)`<br>Sets a property's value to a `boolean`.                                                                      |
    | `void`                                          | `setByteProperty``(java.lang.String name, byte value)`<br>Sets a property's value to a `byte`.                                                                               |
    | `void`                                          | `setDoubleProperty``(java.lang.String name, double value)`<br>Sets a property's value to a `double`.                                                                         |
    | `void`                                          | `setFloatProperty``(java.lang.String name, float value)`<br>Sets a property's value to a `float`.                                                                            |
    | `void`                                          | `setIntProperty``(java.lang.String name, int value)`<br>Sets a property's value to an `integer`.                                                                             |
    | `void`                                          | `setJMSCorrelationID``(java.lang.String correlationID)`<br>Sets this message's correlation ID.                                                                               |
    | `void`                                          | `setJMSCorrelationIDAsBytes``(byte[] correlationID)`<br>Sets this message's correlation ID as an array of bytes.                                                             |
    | `void`                                          | `setJMSDeliveryMode``(int deliveryMode)`<br>Sets this message's delivery mode.                                                                                               |
    | `void`                                          | `setJMSDestination``(`[`Destination`](../../javax/jms/Destination.md)` destination)`<br>Sets this message's destination.                                                     |
    | `void`                                          | `setJMSExpiration``(long expiration)`<br>Sets this message's expiration value.                                                                                               |
    | `void`                                          | `setJMSMessageID``(java.lang.String id)`<br>Sets this message's ID.                                                                                                          |
    | `void`                                          | `setJMSPriority``(int priority)`<br>Sets this message's priority.                                                                                                            |
    | `void`                                          | `setJMSRedelivered``(boolean redelivered)`<br>Sets the indication of whether this message is being redelivered.                                                              |
    | `void`                                          | `setJMSReplyTo``(`[`Destination`](../../javax/jms/Destination.md)` replyTo)`<br>Sets this message's `JMSReplyTo` destination.                                                |
    | `void`                                          | `setJMSTimestamp``(long timestamp)`<br>Sets this message's timestamp.                                                                                                        |
    | `void`                                          | `setJMSType``(java.lang.String type)`<br>Sets this message's type.                                                                                                           |
    | `void`                                          | `setLongProperty``(java.lang.String name, long value)`<br>Sets a property's value to a `long`.                                                                               |
    | `void`                                          | `setObjectProperty``(java.lang.String name, java.lang.Object value)`<br>Sets a property's value to a Java object.                                                            |
    | `void`                                          | `setSenderID``(oracle.jms.AQjmsAgent sender)`<br>Sets this message's sender ID.                                                                                              |
    | `void`                                          | `setShortProperty``(java.lang.String name, short value)`<br>Sets a property's value to a `short`.                                                                            |
    | `void`                                          | `setStringProperty``(java.lang.String name, java.lang.String value)`<br>Sets a property's value to a `String`.                                                               |
    | `java.lang.String`                              | `test_getUserProperties``()`                                                                                                                                                 |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getJMSMessageID

          public java.lang.String getJMSMessageID()
                                           throws JMSException

      Gets this message's ID. The `JMSMessageID` header field contains a value that uniquely identifies each message sent by OJMS. When a message is sent, any previous `JMSMessageID` value is ignored and over-written with a value assigned by OJMS. All `JMSMessageID` values start with the prefix `"ID:"`.
      Specified by:
      [`getJMSMessageID`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Returns:
      the message ID

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message ID is not retrieved due to some error.

      See Also:
      [`Message.setJMSMessageID(String)`](../../javax/jms/Message.md), [`MessageProducer.setDisableMessageID(boolean)`](../../javax/jms/MessageProducer.md)

    <!-- -->

    - #### getJMSMessageIDAsBytes

          public byte[] getJMSMessageIDAsBytes()
                                        throws JMSException

      Gets this message's ID as a byte array.
      Returns:
      the message ID

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message ID is not retrieved due to some error.

    <!-- -->

    - #### setJMSMessageID

          public void setJMSMessageID(java.lang.String id)
                               throws JMSException

      Sets this message's ID. OJMS overwrites a message's `JMSMessageID` header field when the message is sent.
      Specified by:
      [`setJMSMessageID`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `id` - the ID for this message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message ID is not set due to some error.

      See Also:
      [`Message.getJMSMessageID()`](../../javax/jms/Message.md)

    <!-- -->

    - #### getJMSTimestamp

          public long getJMSTimestamp()
                               throws JMSException

      Gets this message's timestamp. The `JMSTimestamp` header field contains the time a message was handed off to a provider to be sent. When a message is sent, any previous `JMSTimestamp` value is ignored and over-written with the time the message was enqueued.
      Specified by:
      [`getJMSTimestamp`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Returns:
      timestamp (format is a normal Java millis time value)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the timestamp is not retrieved due to some error.

      See Also:
      [`Message.setJMSTimestamp(long)`](../../javax/jms/Message.md), [`MessageProducer.setDisableMessageTimestamp(boolean)`](../../javax/jms/MessageProducer.md)

    <!-- -->

    - #### setJMSTimestamp

          public void setJMSTimestamp(long timestamp)
                               throws JMSException

      Sets this message's timestamp. OJMS overwrites a message's `JMSTimestamp` header field when the message is sent.
      Specified by:
      [`setJMSTimestamp`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `timestamp` - the timestamp for this message (format is a normal Java millis time value)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the timestamp is not set due to some error.

      See Also:
      [`Message.getJMSTimestamp()`](../../javax/jms/Message.md)

    <!-- -->

    - #### getJMSCorrelationID

          public java.lang.String getJMSCorrelationID()
                                               throws JMSException

      Gets this message's correlation ID.
      Specified by:
      [`getJMSCorrelationID`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Returns:
      the correlation ID

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the correlation ID is not retrieved due to some error.

      See Also:
      [`Message.setJMSCorrelationID(String)`](../../javax/jms/Message.md), [`Message.getJMSCorrelationIDAsBytes()`](../../javax/jms/Message.md), [`Message.setJMSCorrelationIDAsBytes(byte[])`](../../javax/jms/Message.md)

    <!-- -->

    - #### getJMSCorrelationIDAsBytes

          public byte[] getJMSCorrelationIDAsBytes()
                                            throws JMSException

      Gets this message's correlation ID as an array of bytes.
      Specified by:
      [`getJMSCorrelationIDAsBytes`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Returns:
      the correlation ID for this message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the correlation ID is not retrieved due to some error.

      See Also:
      [`Message.setJMSCorrelationID(String)`](../../javax/jms/Message.md), [`Message.getJMSCorrelationID()`](../../javax/jms/Message.md), [`Message.setJMSCorrelationIDAsBytes(byte[])`](../../javax/jms/Message.md)

    <!-- -->

    - #### setJMSCorrelationID

          public void setJMSCorrelationID(java.lang.String correlationID)
                                   throws JMSException

      Sets this message's correlation ID. A client can use the `JMSCorrelationID` header field to link one message with another.
      Specified by:
      [`setJMSCorrelationID`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `correlationID` - the message ID of a message being referenced

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the correlation ID is not set due to some error.

      See Also:
      [`Message.getJMSCorrelationID()`](../../javax/jms/Message.md), [`Message.getJMSCorrelationIDAsBytes()`](../../javax/jms/Message.md), [`Message.setJMSCorrelationIDAsBytes(byte[])`](../../javax/jms/Message.md)

    <!-- -->

    - #### setJMSCorrelationIDAsBytes

          public void setJMSCorrelationIDAsBytes(byte[] correlationID)
                                          throws JMSException

      Sets this message's correlation ID as an array of bytes.
      Specified by:
      [`setJMSCorrelationIDAsBytes`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `correlationID` - the correlation ID

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the correlation ID is not set due to some error.

      See Also:
      [`Message.setJMSCorrelationID(String)`](../../javax/jms/Message.md), [`Message.getJMSCorrelationID()`](../../javax/jms/Message.md), [`Message.getJMSCorrelationIDAsBytes()`](../../javax/jms/Message.md)

    <!-- -->

    - #### getJMSReplyTo

          public Destination getJMSReplyTo()
                                    throws JMSException

      Gets this message's `JMSReplyTo` destination.
      Specified by:
      [`getJMSReplyTo`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Returns:
      the destination where replies to this message should be sent (an `AQjmsAgent`)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the reply-to destination is not retrieved due to some error.

      See Also:
      [`Message.setJMSReplyTo(Destination)`](../../javax/jms/Message.md)

    <!-- -->

    - #### setJMSReplyTo

          public void setJMSReplyTo(Destination replyTo)
                             throws JMSException

      Sets this message's `JMSReplyTo` destination.
      Specified by:
      [`setJMSReplyTo`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `replyTo` - destination where replies to this message should be sent. Must be an `AQjmsAgent` object (with consumer name and queue/topic address).

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the reply-to destination is not set due to some error.

      See Also:
      [`Message.getJMSReplyTo()`](../../javax/jms/Message.md)

    <!-- -->

    - #### getJMSDestination

          public Destination getJMSDestination()
                                        throws JMSException

      Gets this message's destination. The `JMSDestination` header field contains the destination to which the message is being sent. When a message is sent, any previous `JMSDestination` value is ignored and over-written with the destination specified by the send. When a message is received, its destination value is equivalent to the value assigned when it was sent.
      Specified by:
      [`getJMSDestination`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Returns:
      the destination

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the destination is not retrieved due to some error.

      See Also:
      [`Message.setJMSDestination(Destination)`](../../javax/jms/Message.md)

    <!-- -->

    - #### setJMSDestination

          public void setJMSDestination(Destination destination)
                                 throws JMSException

      Sets this message's destination. OJMS overwrites a message's `JMSDestination` header field when the message is sent.
      Specified by:
      [`setJMSDestination`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `destination` - the destination for this message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the destination is not set due to some error.

      See Also:
      [`Message.getJMSDestination()`](../../javax/jms/Message.md)

    <!-- -->

    - #### getJMSDeliveryMode

          public int getJMSDeliveryMode()
                                 throws JMSException

      Gets this message's delivery mode.
      Specified by:
      [`getJMSDeliveryMode`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Returns:
      the delivery mode

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the delivery mode is not retrieved due to some error.

      See Also:
      [`Message.setJMSDeliveryMode(int)`](../../javax/jms/Message.md), [`DeliveryMode`](../../javax/jms/DeliveryMode.md)

    <!-- -->

    - #### setJMSDeliveryMode

          public void setJMSDeliveryMode(int deliveryMode)
                                  throws JMSException

      Sets this message's delivery mode. OJMS overwrites a message's `JMSDeliveryMode` header field when the message is sent.
      Specified by:
      [`setJMSDeliveryMode`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `deliveryMode` - the delivery mode for this message ([`DeliveryMode.PERSISTENT`](../../javax/jms/DeliveryMode.md) or [`DeliveryMode.NON_PERSISTENT`](../../javax/jms/DeliveryMode.md))

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the delivery mode is not set due to some error.

      See Also:
      [`Message.getJMSDeliveryMode()`](../../javax/jms/Message.md), [`DeliveryMode`](../../javax/jms/DeliveryMode.md)

    <!-- -->

    - #### getJMSRedelivered

          public boolean getJMSRedelivered()
                                    throws JMSException

      Gets an indication of whether this message is being redelivered.
      If a client receives a message with the redelivered indicator set, it is likely, but not guaranteed, that this message was delivered to the client earlier but the client did not commit the transaction (or acknowledge the message).

      Specified by:
      [`getJMSRedelivered`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Returns:
      `true` iff this message is (likely) being redelivered

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the redelivery flag is not retrieved due to some error.

      See Also:
      [`Message.setJMSRedelivered(boolean)`](../../javax/jms/Message.md)

    <!-- -->

    - #### setJMSRedelivered

          public void setJMSRedelivered(boolean redelivered)
                                 throws JMSException

      Sets the indication of whether this message is being redelivered. OJMS overwrites a message's `JMSRedelivered` header field when the message is delivered. This field is set at the time the message is delivered.
      Specified by:
      [`setJMSRedelivered`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `redelivered` - an indication of whether this message is being redelivered

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the redelivery flag is not set due to some error.

      See Also:
      [`Message.getJMSRedelivered()`](../../javax/jms/Message.md)

    <!-- -->

    - #### getJMSType

          public java.lang.String getJMSType()
                                      throws JMSException

      Gets this message's type.
      Specified by:
      [`getJMSType`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Returns:
      the type

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message type is not retrieved due to some error.

      See Also:
      [`Message.setJMSType(String)`](../../javax/jms/Message.md)

    <!-- -->

    - #### setJMSType

          public void setJMSType(java.lang.String type)
                          throws JMSException

      Sets this message's type.
      Specified by:
      [`setJMSType`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `type` - the type for this message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message type is not set due to some error.

      See Also:
      [`Message.getJMSType()`](../../javax/jms/Message.md)

    <!-- -->

    - #### getJMSExpiration

          public long getJMSExpiration()
                                throws JMSException

      Gets this message's expiration value. OJMS overwrites a message's `JMSExpiration` header field when the message is sent. If the time-to-live is specified as zero, OJMS sets `JMSExpiration` to zero (which indicates that the message does not expire). Otherwise OJMS sets `JMSExpiration` to the sum of the time-to-live value specified by the client and the GMT at the time of the send. When a message's expiration time is reached, the message is moved to the exception queue corresponding to the destination queue/topic.
      Specified by:
      [`getJMSExpiration`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Returns:
      the time the message expires (format is a normal Java millis time value)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the expiration value is not retrieved due to some error.

      See Also:
      [`Message.setJMSExpiration(long)`](../../javax/jms/Message.md)

    <!-- -->

    - #### setJMSExpiration

          public void setJMSExpiration(long expiration)
                                throws JMSException

      Sets this message's expiration value. OJMS overwrites a message's `JMSExpiration` header field when the message is sent.
      Specified by:
      [`setJMSExpiration`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `expiration` - the expiration value for this message (format is a normal Java millis time value)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the expiration value is not set due to some error.

      See Also:
      [`Message.getJMSExpiration()`](../../javax/jms/Message.md)

    <!-- -->

    - #### getJMSPriority

          public int getJMSPriority()
                             throws JMSException

      Gets this message's priority. JMS defines a ten level priority value with 0 as the lowest priority and 9 as the highest.
      Specified by:
      [`getJMSPriority`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Returns:
      the priority

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the priority is not retrieved due to some error.

      See Also:
      [`Message.setJMSPriority(int)`](../../javax/jms/Message.md)

    <!-- -->

    - #### setJMSPriority

          public void setJMSPriority(int priority)
                              throws JMSException

      Sets this message's priority. JMS defines a ten level priority value with 0 as the lowest priority and 9 as the highest. OJMS overwrites a message's `JMSPriority` header field when the message is sent.
      Specified by:
      [`setJMSPriority`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `priority` - the priority for this message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the priority is not set due to some error.

      See Also:
      [`Message.getJMSPriority()`](../../javax/jms/Message.md)

    <!-- -->

    - #### clearProperties

          public void clearProperties()
                               throws JMSException

      Clears a message's properties.
      Specified by:
      [`clearProperties`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message properties are not cleared due to some error.

    <!-- -->

    - #### propertyExists

          public boolean propertyExists(java.lang.String name)
                                 throws JMSException

      Checks if a property value exists.
      Specified by:
      [`propertyExists`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property to check

      Returns:
      `true` iff the property exists

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property's existence is not checked due to some error.

    <!-- -->

    - #### getBooleanProperty

          public boolean getBooleanProperty(java.lang.String name)
                                     throws JMSException

      Returns a property value as a `boolean`.
      Specified by:
      [`getBooleanProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      Returns:
      the property's value, converted (if needed) to a `boolean`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not retrieved due to some error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if the conversion is invalid.

    <!-- -->

    - #### getByteProperty

          public byte getByteProperty(java.lang.String name)
                               throws JMSException

      Returns a property value as a `byte`.
      Specified by:
      [`getByteProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      Returns:
      the property's value, converted (if needed) to a `byte`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not retrieved due to some error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if the conversion is invalid.

    <!-- -->

    - #### getShortProperty

          public short getShortProperty(java.lang.String name)
                                 throws JMSException

      Returns a property value as a `short`.
      Specified by:
      [`getShortProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      Returns:
      the property's value, converted (if needed) to a `short`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not retrieved due to some error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if the conversion is invalid.

    <!-- -->

    - #### getIntProperty

          public int getIntProperty(java.lang.String name)
                             throws JMSException

      Returns a property value as an `int`.
      Specified by:
      [`getIntProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      Returns:
      the property's value, converted (if needed) to an `int`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not retrieved due to some error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if the conversion is invalid.

    <!-- -->

    - #### getLongProperty

          public long getLongProperty(java.lang.String name)
                               throws JMSException

      Returns a property value as a `long`.
      Specified by:
      [`getLongProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      Returns:
      the property's value, converted (if needed) to a `long`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not retrieved due to some error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if the conversion is invalid.

    <!-- -->

    - #### getFloatProperty

          public float getFloatProperty(java.lang.String name)
                                 throws JMSException

      Returns a property value as a `float`.
      Specified by:
      [`getFloatProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      Returns:
      the property's value, converted (if needed) to a `float`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not retrieved due to some error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if the conversion is invalid.

    <!-- -->

    - #### getDoubleProperty

          public double getDoubleProperty(java.lang.String name)
                                   throws JMSException

      Returns a property value as a `double`.
      Specified by:
      [`getDoubleProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      Returns:
      the property's value, converted (if needed) to a `double`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not retrieved due to some error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if the conversion is invalid.

    <!-- -->

    - #### getStringProperty

          public java.lang.String getStringProperty(java.lang.String name)
                                             throws JMSException

      Returns a property value as a `String`.
      Specified by:
      [`getStringProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      Returns:
      the property's value, converted (if needed) to a `String`, or `null` if there is no such property

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not retrieved due to some error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if the conversion is invalid.

    <!-- -->

    - #### getObjectProperty

          public java.lang.Object getObjectProperty(java.lang.String name)
                                             throws JMSException

      Returns a property value as a Java object. Note that this method can be used to return, in objectified format, a value that has been stored as a property in the message with the `setObjectProperty` method or the format's equivalent primitive `set`*type*`Property` method.
      Specified by:
      [`getObjectProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      Returns:
      the property's value, converted (if needed) to objectified format (e.g., `int` is converted to `Integer`), or `null` if there is no such property

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not retrieved due to some error.

    <!-- -->

    - #### getPropertyNames

          public java.util.Enumeration getPropertyNames()
                                                 throws JMSException

      Returns an `Enumeration` of all the property names.
      Specified by:
      [`getPropertyNames`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Returns:
      the enumeration

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the enumeration is not retrieved due to some error.

    <!-- -->

    - #### getUserPropertyNames

          public java.util.Enumeration getUserPropertyNames()
                                                     throws JMSException

      Returns an `Enumeration` of all the user property names.
      Returns:
      the enumeration

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the enumeration is not retrieved due to some error.

    <!-- -->

    - #### setBooleanProperty

          public void setBooleanProperty(java.lang.String name,
                                         boolean value)
                                  throws JMSException

      Sets a property's value to a `boolean`. If the property does not already exist, it is added to this message.
      Specified by:
      [`setBooleanProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      `value` - the value for the property

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not set due to some error.

      `java.lang.IllegalArgumentException` - if the name is `null` or is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only.

    <!-- -->

    - #### setByteProperty

          public void setByteProperty(java.lang.String name,
                                      byte value)
                               throws JMSException

      Sets a property's value to a `byte`. If the property does not already exist, it is added to this message.
      Specified by:
      [`setByteProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      `value` - the value for the property

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not set due to some error.

      `java.lang.IllegalArgumentException` - if the name is `null` or is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only.

    <!-- -->

    - #### setShortProperty

          public void setShortProperty(java.lang.String name,
                                       short value)
                                throws JMSException

      Sets a property's value to a `short`. If the property does not already exist, it is added to this message.
      Specified by:
      [`setShortProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      `value` - the value for the property

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not set due to some error.

      `java.lang.IllegalArgumentException` - if the name is `null` or is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only.

    <!-- -->

    - #### setIntProperty

          public void setIntProperty(java.lang.String name,
                                     int value)
                              throws JMSException

      Sets a property's value to an `integer`. If the property does not already exist, it is added to this message.
      Specified by:
      [`setIntProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      `value` - the value for the property

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not set due to some error.

      `java.lang.IllegalArgumentException` - if the name is `null` or is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only.

    <!-- -->

    - #### setLongProperty

          public void setLongProperty(java.lang.String name,
                                      long value)
                               throws JMSException

      Sets a property's value to a `long`. If the property does not already exist, it is added to this message.
      Specified by:
      [`setLongProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      `value` - the value for the property

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not set due to some error.

      `java.lang.IllegalArgumentException` - if the name is `null` or is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only.

    <!-- -->

    - #### setFloatProperty

          public void setFloatProperty(java.lang.String name,
                                       float value)
                                throws JMSException

      Sets a property's value to a `float`. If the property does not already exist, it is added to this message.
      Specified by:
      [`setFloatProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      `value` - the value for the property

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not set due to some error.

      `java.lang.IllegalArgumentException` - if the name is `null` or is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only.

    <!-- -->

    - #### setDoubleProperty

          public void setDoubleProperty(java.lang.String name,
                                        double value)
                                 throws JMSException

      Sets a property's value to a `double`. If the property does not already exist, it is added to this message.
      Specified by:
      [`setDoubleProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      `value` - the value for the property

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not set due to some error.

      `java.lang.IllegalArgumentException` - if the name is `null` or is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only.

    <!-- -->

    - #### setStringProperty

          public void setStringProperty(java.lang.String name,
                                        java.lang.String value)
                                 throws JMSException

      Sets a property's value to a `String`. If the property does not already exist, it is added to this message.
      Specified by:
      [`setStringProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      `value` - the value for the property

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not set due to some error.

      `java.lang.IllegalArgumentException` - if the name is `null` or is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only.

    <!-- -->

    - #### setObjectProperty

          public void setObjectProperty(java.lang.String name,
                                        java.lang.Object value)
                                 throws JMSException

      Sets a property's value to a Java object. If the property does not already exist, it is added to this message.
      Specified by:
      [`setObjectProperty`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Parameters:
      `name` - the name of the property

      `value` - the value for the property - must be an objectified primitive (e.g., an `Integer`) or a `String`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the property is not set due to some error.

      `java.lang.IllegalArgumentException` - if the name is `null` or is an empty string.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if `value` is `null` or is neither an objectified primitive nor a `String`.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if properties are read-only.

    <!-- -->

    - #### acknowledge

          public void acknowledge()
                           throws JMSException

      Acknowleges message receipt when using the `CLIENT_ACKNOWLEDGE` mode.
      Specified by:
      [`acknowledge`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if SQL exceptions occur during transaction commit.

      See Also:
      [`Session.CLIENT_ACKNOWLEDGE`](../../javax/jms/Session.md)

    <!-- -->

    - #### clearBody

          public void clearBody()
                         throws JMSException

      Clears out the message body. All other parts of the message are left untouched.
      Specified by:
      [`clearBody`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message body is not cleared due to some error.

    <!-- -->

    - #### getSenderID

          public oracle.jms.AQjmsAgent getSenderID()
                                            throws JMSException

      Gets this message's sender ID. This value is available only if it was set by the sender before sending the message.
      Returns:
      `AQjmsAgent` representing sender

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the sender ID is not retrieved due to some error.

    <!-- -->

    - #### setSenderID

          public void setSenderID(oracle.jms.AQjmsAgent sender)
                           throws JMSException

      Sets this message's sender ID.
      Parameters:
      `sender` - `AQjmsAgent` representing sender

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the SenderID is not set due to some error.

    <!-- -->

    - #### getAttempts

          public int getAttempts()
                          throws JMSException

      Gets this message's retry count.
      Returns:
      the number of attempts already made (always one less than the `JMSXDeliveryCount` property)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the retry count can not be retrieved due to some error.

    <!-- -->

    - #### test_getUserProperties

          public java.lang.String test_getUserProperties()
                                                  throws JMSException

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md)

    <!-- -->

    - #### getBodyLength

          public long getBodyLength()
                             throws JMSException

      Gets the number of bytes of the message body when the message is in read-only mode. The value returned can be used to allocate a byte array. The value returned is the entire length of the message body, regardless of where the pointer for reading the message is currently located. This method returns the accurate value for the BytesMessage always. However, when the streaming is enabled by the client, this method returns the number of bytes of the message body for StreamMessage as well.
      Returns:
      number of bytes in the message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

    <!-- -->

    - #### isLargeBody

          public boolean isLargeBody()

      This method can be used by the client applications to check whether the message contains large messaege body and hence requires streaming with dequeue.
      Returns:
      true when the message body is large and server decides to stream the payload with dequeue

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

- [Prev Class](AQjmsMapMessage.md)
- [Next Class](AQjmsObjectMessage.md)

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
