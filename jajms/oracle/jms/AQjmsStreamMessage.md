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

- [Prev Class](AQjmsSession.md)
- [Next Class](AQjmsTextMessage.md)

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

## Class AQjmsStreamMessage

- java.lang.Object

- - [oracle.jms.AQjmsMessage](AQjmsMessage.md)

  - - oracle.jms.AQjmsStreamMessage

<!-- -->

- All Implemented Interfaces:
  [Message](../../javax/jms/Message.md), [StreamMessage](../../javax/jms/StreamMessage.md)

  ------------------------------------------------------------------------



      public class AQjmsStreamMessage
      extends AQjmsMessage
      implements StreamMessage

  Oracle class implementing javax.jms.StreamMessage

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Message](../../javax/jms/Message.md)

      [`DEFAULT_DELIVERY_MODE`](../../javax/jms/Message.md)`, `[`DEFAULT_PRIORITY`](../../javax/jms/Message.md)`, `[`DEFAULT_TIME_TO_LIVE`](../../javax/jms/Message.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type      | Method and Description                                                                                                                                           |
    |------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                 | `clearBody``()`<br>Clear out the message body.                                                                                                                   |
    | `java.io.OutputStream` | `getBody``(java.io.OutputStream outputStream)`<br>Writes the message body to the OutputStream specified.                                                         |
    | `java.io.OutputStream` | `getBody``(java.io.OutputStream outputStream, int chunkSize)`<br>Writes the message body to the OutputStream specified, with chunkSize bytes written at a time.  |
    | `java.io.OutputStream` | `getBody``(java.io.OutputStream outputStream, int chunkSize, long timeout)`<br>Writes the message body to the OutputStream specified, chunkSize bytes at a time. |
    | `java.io.OutputStream` | `getBody``(java.io.OutputStream outputStream, long timeout)`<br>Writes the message body to the OutputStream specified.                                           |
    | `boolean`              | `readBoolean``()`<br>Reads a `boolean` from the stream message.                                                                                                  |
    | `byte`                 | `readByte``()`<br>Reads a `byte` value from the stream message.                                                                                                  |
    | `int`                  | `readBytes``(byte[] value)`<br>Reads a byte array field from the stream message into the specified `byte[]` object (the read buffer).                            |
    | `char`                 | `readChar``()`<br>Reads a Unicode character value from the stream message.                                                                                       |
    | `double`               | `readDouble``()`<br>Reads a `double` from the stream message.                                                                                                    |
    | `float`                | `readFloat``()`<br>Reads a `float` from the stream message.                                                                                                      |
    | `int`                  | `readInt``()`<br>Reads a 32-bit integer from the stream message.                                                                                                 |
    | `long`                 | `readLong``()`<br>Reads a 64-bit integer from the stream message.                                                                                                |
    | `java.lang.Object`     | `readObject``()`<br>Reads an object from the stream message.                                                                                                     |
    | `short`                | `readShort``()`<br>Reads a 16-bit integer from the stream message.                                                                                               |
    | `java.lang.String`     | `readString``()`<br>Reads a `String` from the stream message.                                                                                                    |
    | `void`                 | `reset``()`<br>Puts the message body in read-only mode and repositions the stream to the beginning.                                                              |
    | `void`                 | `setInputStream``(java.io.InputStream inputStream)`<br>Writes an InputStream to the bytes message stream                                                         |
    | `void`                 | `writeBoolean``(boolean value)`<br>Writes a `boolean` to the stream message.                                                                                     |
    | `void`                 | `writeByte``(byte value)`<br>Writes a `byte` to the stream message.                                                                                              |
    | `void`                 | `writeBytes``(byte[] value)`<br>Writes a byte array field to the stream message.                                                                                 |
    | `void`                 | `writeBytes``(byte[] value, int offset, int length)`<br>Writes a portion of a byte array as a byte array field to the stream message.                            |
    | `void`                 | `writeChar``(char value)`<br>Writes a `char` to the stream message.                                                                                              |
    | `void`                 | `writeDouble``(double value)`<br>Writes a `double` to the stream message.                                                                                        |
    | `void`                 | `writeFloat``(float value)`<br>Writes a `float` to the stream message.                                                                                           |
    | `void`                 | `writeInt``(int value)`<br>Writes an `int` to the stream message.                                                                                                |
    | `void`                 | `writeLong``(long value)`<br>Writes a `long` to the stream message.                                                                                              |
    | `void`                 | `writeObject``(java.lang.Object value)`<br>Writes an object to the stream message.                                                                               |
    | `void`                 | `writeShort``(short value)`<br>Writes a `short` to the stream message.                                                                                           |
    | `void`                 | `writeString``(java.lang.String value)`<br>Writes a `String` to the stream message.                                                                              |

    - ### Methods inherited from class oracle.jms.[AQjmsMessage](AQjmsMessage.md)

      [`acknowledge`](AQjmsMessage.md)`, `[`clearProperties`](AQjmsMessage.md)`, `[`getAttempts`](AQjmsMessage.md)`, `[`getBodyLength`](AQjmsMessage.md)`, `[`getBooleanProperty`](AQjmsMessage.md)`, `[`getByteProperty`](AQjmsMessage.md)`, `[`getDoubleProperty`](AQjmsMessage.md)`, `[`getFloatProperty`](AQjmsMessage.md)`, `[`getIntProperty`](AQjmsMessage.md)`, `[`getJMSCorrelationID`](AQjmsMessage.md)`, `[`getJMSCorrelationIDAsBytes`](AQjmsMessage.md)`, `[`getJMSDeliveryMode`](AQjmsMessage.md)`, `[`getJMSDestination`](AQjmsMessage.md)`, `[`getJMSExpiration`](AQjmsMessage.md)`, `[`getJMSMessageID`](AQjmsMessage.md)`, `[`getJMSMessageIDAsBytes`](AQjmsMessage.md)`, `[`getJMSPriority`](AQjmsMessage.md)`, `[`getJMSRedelivered`](AQjmsMessage.md)`, `[`getJMSReplyTo`](AQjmsMessage.md)`, `[`getJMSTimestamp`](AQjmsMessage.md)`, `[`getJMSType`](AQjmsMessage.md)`, `[`getLongProperty`](AQjmsMessage.md)`, `[`getObjectProperty`](AQjmsMessage.md)`, `[`getPropertyNames`](AQjmsMessage.md)`, `[`getSenderID`](AQjmsMessage.md)`, `[`getShortProperty`](AQjmsMessage.md)`, `[`getStringProperty`](AQjmsMessage.md)`, `[`getUserPropertyNames`](AQjmsMessage.md)`, `[`isLargeBody`](AQjmsMessage.md)`, `[`propertyExists`](AQjmsMessage.md)`, `[`setBooleanProperty`](AQjmsMessage.md)`, `[`setByteProperty`](AQjmsMessage.md)`, `[`setDoubleProperty`](AQjmsMessage.md)`, `[`setFloatProperty`](AQjmsMessage.md)`, `[`setIntProperty`](AQjmsMessage.md)`, `[`setJMSCorrelationID`](AQjmsMessage.md)`, `[`setJMSCorrelationIDAsBytes`](AQjmsMessage.md)`, `[`setJMSDeliveryMode`](AQjmsMessage.md)`, `[`setJMSDestination`](AQjmsMessage.md)`, `[`setJMSExpiration`](AQjmsMessage.md)`, `[`setJMSMessageID`](AQjmsMessage.md)`, `[`setJMSPriority`](AQjmsMessage.md)`, `[`setJMSRedelivered`](AQjmsMessage.md)`, `[`setJMSReplyTo`](AQjmsMessage.md)`, `[`setJMSTimestamp`](AQjmsMessage.md)`, `[`setJMSType`](AQjmsMessage.md)`, `[`setLongProperty`](AQjmsMessage.md)`, `[`setObjectProperty`](AQjmsMessage.md)`, `[`setSenderID`](AQjmsMessage.md)`, `[`setShortProperty`](AQjmsMessage.md)`, `[`setStringProperty`](AQjmsMessage.md)`, `[`test_getUserProperties`](AQjmsMessage.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface javax.jms.[Message](../../javax/jms/Message.md)

      [`acknowledge`](../../javax/jms/Message.md)`, `[`clearProperties`](../../javax/jms/Message.md)`, `[`getBooleanProperty`](../../javax/jms/Message.md)`, `[`getByteProperty`](../../javax/jms/Message.md)`, `[`getDoubleProperty`](../../javax/jms/Message.md)`, `[`getFloatProperty`](../../javax/jms/Message.md)`, `[`getIntProperty`](../../javax/jms/Message.md)`, `[`getJMSCorrelationID`](../../javax/jms/Message.md)`, `[`getJMSCorrelationIDAsBytes`](../../javax/jms/Message.md)`, `[`getJMSDeliveryMode`](../../javax/jms/Message.md)`, `[`getJMSDestination`](../../javax/jms/Message.md)`, `[`getJMSExpiration`](../../javax/jms/Message.md)`, `[`getJMSMessageID`](../../javax/jms/Message.md)`, `[`getJMSPriority`](../../javax/jms/Message.md)`, `[`getJMSRedelivered`](../../javax/jms/Message.md)`, `[`getJMSReplyTo`](../../javax/jms/Message.md)`, `[`getJMSTimestamp`](../../javax/jms/Message.md)`, `[`getJMSType`](../../javax/jms/Message.md)`, `[`getLongProperty`](../../javax/jms/Message.md)`, `[`getObjectProperty`](../../javax/jms/Message.md)`, `[`getPropertyNames`](../../javax/jms/Message.md)`, `[`getShortProperty`](../../javax/jms/Message.md)`, `[`getStringProperty`](../../javax/jms/Message.md)`, `[`propertyExists`](../../javax/jms/Message.md)`, `[`setBooleanProperty`](../../javax/jms/Message.md)`, `[`setByteProperty`](../../javax/jms/Message.md)`, `[`setDoubleProperty`](../../javax/jms/Message.md)`, `[`setFloatProperty`](../../javax/jms/Message.md)`, `[`setIntProperty`](../../javax/jms/Message.md)`, `[`setJMSCorrelationID`](../../javax/jms/Message.md)`, `[`setJMSCorrelationIDAsBytes`](../../javax/jms/Message.md)`, `[`setJMSDeliveryMode`](../../javax/jms/Message.md)`, `[`setJMSDestination`](../../javax/jms/Message.md)`, `[`setJMSExpiration`](../../javax/jms/Message.md)`, `[`setJMSMessageID`](../../javax/jms/Message.md)`, `[`setJMSPriority`](../../javax/jms/Message.md)`, `[`setJMSRedelivered`](../../javax/jms/Message.md)`, `[`setJMSReplyTo`](../../javax/jms/Message.md)`, `[`setJMSTimestamp`](../../javax/jms/Message.md)`, `[`setJMSType`](../../javax/jms/Message.md)`, `[`setLongProperty`](../../javax/jms/Message.md)`, `[`setObjectProperty`](../../javax/jms/Message.md)`, `[`setShortProperty`](../../javax/jms/Message.md)`, `[`setStringProperty`](../../javax/jms/Message.md)

<!-- -->

- - ### Method Detail

    - #### readBoolean

          public boolean readBoolean()
                              throws JMSException

      Reads a `boolean` from the stream message.
      Specified by:
      [`readBoolean`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Returns:
      the `boolean` value read

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readByte

          public byte readByte()
                        throws JMSException

      Reads a `byte` value from the stream message.
      Specified by:
      [`readByte`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Returns:
      the next byte from the stream message as a 8-bit `byte`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readShort

          public short readShort()
                          throws JMSException

      Reads a 16-bit integer from the stream message.
      Specified by:
      [`readShort`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Returns:
      a 16-bit integer from the stream message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readChar

          public char readChar()
                        throws JMSException

      Reads a Unicode character value from the stream message.
      Specified by:
      [`readChar`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Returns:
      a Unicode character from the stream message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readInt

          public int readInt()
                      throws JMSException

      Reads a 32-bit integer from the stream message.
      Specified by:
      [`readInt`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Returns:
      a 32-bit integer value from the stream message, interpreted as an `int`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readLong

          public long readLong()
                        throws JMSException

      Reads a 64-bit integer from the stream message.
      Specified by:
      [`readLong`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Returns:
      a 64-bit integer value from the stream message, interpreted as a `long`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readFloat

          public float readFloat()
                          throws JMSException

      Reads a `float` from the stream message.
      Specified by:
      [`readFloat`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Returns:
      a `float` value from the stream message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readDouble

          public double readDouble()
                            throws JMSException

      Reads a `double` from the stream message.
      Specified by:
      [`readDouble`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Returns:
      a `double` value from the stream message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readString

          public java.lang.String readString()
                                      throws JMSException

      Reads a `String` from the stream message.
      Specified by:
      [`readString`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Returns:
      a Unicode string from the stream message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readBytes

          public int readBytes(byte[] value)
                        throws JMSException

      Reads a byte array field from the stream message into the specified `byte[]` object (the read buffer).
      To read the field value, `readBytes` should be successively called until it returns a value less than the length of the read buffer. The value of the bytes in the buffer following the last byte read is undefined.

      If `readBytes` returns a value equal to the length of the buffer, a subsequent `readBytes` call must be made. If there are no more bytes to be read, this call returns -1.

      If the byte array field value is null, `readBytes` returns -1.

      If the byte array field value is empty, `readBytes` returns 0.

      Once the first `readBytes` call on a `byte[]` field value has been made, the full value of the field must be read before it is valid to read the next field. An attempt to read the next field before that has been done will throw a `MessageFormatException`.

      To read the byte field value into a new `byte[]` object, use the `readObject` method.

      Specified by:
      [`readBytes`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Parameters:
      `value` - the buffer into which the data is read

      Returns:
      the total number of bytes read into the buffer, or -1 if there is no more data because the end of the byte field has been reached

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

      See Also:
      `AQjmsStreamMessage.readObject()`

    <!-- -->

    - #### readObject

          public java.lang.Object readObject()
                                      throws JMSException

      Reads an object from the stream message.
      This method can be used to return, in objectified format, an object in the Java programming language ("Java object") that has been written to the stream with the equivalent `writeObject` method call, or its equivalent primitive `write`*`type`* method.

      Note that byte values are returned as `byte[]`, not `Byte[]`.

      An attempt to call `readObject` to read a byte field value into a new `byte[]` object before the full value of the byte field has been read will throw a `MessageFormatException`.

      Specified by:
      [`readObject`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Returns:
      a Java object from the stream message, in objectified format (for example, if the object was written as an `int`, an `Integer` is returned)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

      See Also:
      `AQjmsStreamMessage.readBytes(byte[] value)`

    <!-- -->

    - #### writeBoolean

          public void writeBoolean(boolean value)
                            throws JMSException

      Writes a `boolean` to the stream message. The value `true` is written as the value `(byte)1`; the value `false` is written as the value `(byte)0`.
      Specified by:
      [`writeBoolean`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Parameters:
      `value` - the `boolean` value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeByte

          public void writeByte(byte value)
                         throws JMSException

      Writes a `byte` to the stream message.
      Specified by:
      [`writeByte`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Parameters:
      `value` - the `byte` value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeShort

          public void writeShort(short value)
                          throws JMSException

      Writes a `short` to the stream message.
      Specified by:
      [`writeShort`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Parameters:
      `value` - the `short` value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeChar

          public void writeChar(char value)
                         throws JMSException

      Writes a `char` to the stream message.
      Specified by:
      [`writeChar`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Parameters:
      `value` - the `char` value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeInt

          public void writeInt(int value)
                        throws JMSException

      Writes an `int` to the stream message.
      Specified by:
      [`writeInt`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Parameters:
      `value` - the `int` value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeLong

          public void writeLong(long value)
                         throws JMSException

      Writes a `long` to the stream message.
      Specified by:
      [`writeLong`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Parameters:
      `value` - the `long` value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeFloat

          public void writeFloat(float value)
                          throws JMSException

      Writes a `float` to the stream message.
      Specified by:
      [`writeFloat`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Parameters:
      `value` - the `float` value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeDouble

          public void writeDouble(double value)
                           throws JMSException

      Writes a `double` to the stream message.
      Specified by:
      [`writeDouble`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Parameters:
      `value` - the `double` value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeString

          public void writeString(java.lang.String value)
                           throws JMSException

      Writes a `String` to the stream message.
      Specified by:
      [`writeString`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Parameters:
      `value` - the `String` value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeBytes

          public void writeBytes(byte[] value)
                          throws JMSException

      Writes a byte array field to the stream message.
      The byte array `value` is written to the message as a byte array field. Consecutively written byte array fields are treated as two distinct fields when the fields are read.

      Specified by:
      [`writeBytes`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Parameters:
      `value` - the byte array value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeBytes

          public void writeBytes(byte[] value,
                                 int offset,
                                 int length)
                          throws JMSException

      Writes a portion of a byte array as a byte array field to the stream message.
      The a portion of the byte array `value` is written to the message as a byte array field. Consecutively written byte array fields are treated as two distinct fields when the fields are read.

      Specified by:
      [`writeBytes`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Parameters:
      `value` - the byte array value to be written

      `offset` - the initial offset within the byte array

      `length` - the number of bytes to use

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeObject

          public void writeObject(java.lang.Object value)
                           throws JMSException

      Writes an object to the stream message.
      This method works only for the objectified primitive object types (`Integer`, `Double`, `Long` ...), `String` objects, and byte arrays.

      Specified by:
      [`writeObject`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Parameters:
      `value` - the Java object to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if the object is invalid.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setInputStream

          public void setInputStream(java.io.InputStream inputStream)
                              throws JMSException

      Writes an InputStream to the bytes message stream
      Parameters:
      `inputStream` - - InputStream to read the message payload

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - - if the JMS provided fails to read the payload due to some internal error

    <!-- -->

    - #### getBody

          public java.io.OutputStream getBody(java.io.OutputStream outputStream)
                                       throws JMSException

      Writes the message body to the OutputStream specified.
      Parameters:
      `outputStream` - - the OutputStream to which message body can be written

      Returns:
      the OutputStream containing the message body.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - - if the JMS provided fails to receive the message body due to some internal error

    <!-- -->

    - #### getBody

          public java.io.OutputStream getBody(java.io.OutputStream outputStream,
                                              int chunkSize)
                                       throws JMSException

      Writes the message body to the OutputStream specified, with chunkSize bytes written at a time.
      Parameters:
      `outputStream` - - the OutputStream to which message body can be written

      `chunkSize` - - the number of bytes to be written at a time, default value 8192 (ie. 8KB)

      Returns:
      the OutputStream containing the message body.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - - if the JMS provided fails to receive the message body due to some internal error

    <!-- -->

    - #### getBody

          public java.io.OutputStream getBody(java.io.OutputStream outputStream,
                                              long timeout)
                                       throws JMSException

      Writes the message body to the OutputStream specified. This method waits until the message body is written completely to the OutputStream or the timeout expires. A timeout of zero never expires, and a timeout of negative value is ignored.
      Parameters:
      `outputStream` - - the OutputStream to which message body can be written

      `timeout` - - the timeout value (in milliseconds)

      Returns:
      the OutputStream containing the message body.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - - if the JMS provided fails to receive the message body due to some internal error

    <!-- -->

    - #### getBody

          public java.io.OutputStream getBody(java.io.OutputStream outputStream,
                                              int chunkSize,
                                              long timeout)
                                       throws JMSException

      Writes the message body to the OutputStream specified, chunkSize bytes at a time. This method waits until the message body is written completely to the OutputStream or the timeout expires. A timeout of zero never expires, and a timeout of negative value is ignored.
      Parameters:
      `outputStream` - - the OutputStream to which message body can be written

      `chunkSize` - - the number of bytes to be written at a time, default value 8192 (ie. 8KB)

      `timeout` - - the timeout value (in milliseconds)

      Returns:
      the OutputStream containing the message body.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - - if the JMS provided fails to receive the message body due to some internal error

    <!-- -->

    - #### reset

          public void reset()
                     throws JMSException

      Puts the message body in read-only mode and repositions the stream to the beginning.
      Specified by:
      [`reset`](../../javax/jms/StreamMessage.md) in interface [`StreamMessage`](../../javax/jms/StreamMessage.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to reset the message due to some internal error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if the message has an invalid format.

    <!-- -->

    - #### clearBody

          public void clearBody()
                         throws JMSException

      Clear out the message body. All other parts of the message are left untouched.
      Specified by:
      [`clearBody`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`clearBody`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to due to some internal JMS error.

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

- [Prev Class](AQjmsSession.md)
- [Next Class](AQjmsTextMessage.md)

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
