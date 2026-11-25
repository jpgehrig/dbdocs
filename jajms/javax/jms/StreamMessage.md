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

- [Prev Class](Session.md)
- [Next Class](TemporaryQueue.md)

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

## Interface StreamMessage

- All Superinterfaces:
  [Message](Message.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsStreamMessage](../../oracle/jms/AQjmsStreamMessage.md)

  ------------------------------------------------------------------------



      public interface StreamMessage
      extends Message

  A `StreamMessage` object is used to send a stream of primitive types in the Java programming language. It is filled and read sequentially. It inherits from the `Message` interface and adds a stream message body. Its methods are based largely on those found in `java.io.DataInputStream` and `java.io.DataOutputStream`.
  The primitive types can be read or written explicitly using methods for each type. They may also be read or written generically as objects. For instance, a call to `StreamMessage.writeInt(6)` is equivalent to `StreamMessage.writeObject(new Integer(6))`. Both forms are provided, because the explicit form is convenient for static programming, and the object form is needed when types are not known at compile time.

  When the message is first created, and when `clearBody` is called, the body of the message is in write-only mode. After the first call to `reset` has been made, the message body is in read-only mode. After a message has been sent, the client that sent it can retain and modify it without affecting the message that has been sent. The same message object can be sent multiple times. When a message has been received, the provider has called `reset` so that the message body is in read-only mode for the client.

  If `clearBody` is called on a message in read-only mode, the message body is cleared and the message body is in write-only mode.

  If a client attempts to read a message in write-only mode, a `MessageNotReadableException` is thrown.

  If a client attempts to write a message in read-only mode, a `MessageNotWriteableException` is thrown.

  `StreamMessage` objects support the following conversion table. The marked cases must be supported. The unmarked cases must throw a `JMSException`. The `String`-to-primitive conversions may throw a runtime exception if the primitive's `valueOf()` method does not accept it as a valid `String` representation of the primitive.

  A value written as the row type can be read as the column type.

       |        | boolean byte short char int long float double String byte[]
       |----------------------------------------------------------------------
       |boolean |    X                                            X
       |byte    |          X     X         X   X                  X
       |short   |                X         X   X                  X
       |char    |                     X                           X
       |int     |                          X   X                  X
       |long    |                              X                  X
       |float   |                                    X     X      X
       |double  |                                          X      X
       |String  |    X     X     X         X   X     X     X      X
       |byte[]  |                                                        X
       |----------------------------------------------------------------------


  Attempting to read a null value as a primitive type must be treated as calling the primitive's corresponding `valueOf(String)` conversion method with a null value. Since `char` does not support a `String` conversion, attempting to read a null value as a `char` must throw a `NullPointerException`.

  See Also:
  [`Session.createStreamMessage()`](Session.md), [`BytesMessage`](BytesMessage.md), [`MapMessage`](MapMessage.md), [`Message`](Message.md), [`ObjectMessage`](ObjectMessage.md), [`TextMessage`](TextMessage.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Message](Message.md)

      [`DEFAULT_DELIVERY_MODE`](Message.md)`, `[`DEFAULT_PRIORITY`](Message.md)`, `[`DEFAULT_TIME_TO_LIVE`](Message.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                |
    |--------------------|---------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`          | `readBoolean``()`<br>Reads a `boolean` from the stream message.                                                                       |
    | `byte`             | `readByte``()`<br>Reads a `byte` value from the stream message.                                                                       |
    | `int`              | `readBytes``(byte[] value)`<br>Reads a byte array field from the stream message into the specified `byte[]` object (the read buffer). |
    | `char`             | `readChar``()`<br>Reads a Unicode character value from the stream message.                                                            |
    | `double`           | `readDouble``()`<br>Reads a `double` from the stream message.                                                                         |
    | `float`            | `readFloat``()`<br>Reads a `float` from the stream message.                                                                           |
    | `int`              | `readInt``()`<br>Reads a 32-bit integer from the stream message.                                                                      |
    | `long`             | `readLong``()`<br>Reads a 64-bit integer from the stream message.                                                                     |
    | `java.lang.Object` | `readObject``()`<br>Reads an object from the stream message.                                                                          |
    | `short`            | `readShort``()`<br>Reads a 16-bit integer from the stream message.                                                                    |
    | `java.lang.String` | `readString``()`<br>Reads a `String` from the stream message.                                                                         |
    | `void`             | `reset``()`<br>Puts the message body in read-only mode and repositions the stream to the beginning.                                   |
    | `void`             | `writeBoolean``(boolean value)`<br>Writes a `boolean` to the stream message.                                                          |
    | `void`             | `writeByte``(byte value)`<br>Writes a `byte` to the stream message.                                                                   |
    | `void`             | `writeBytes``(byte[] value)`<br>Writes a byte array field to the stream message.                                                      |
    | `void`             | `writeBytes``(byte[] value, int offset, int length)`<br>Writes a portion of a byte array as a byte array field to the stream message. |
    | `void`             | `writeChar``(char value)`<br>Writes a `char` to the stream message.                                                                   |
    | `void`             | `writeDouble``(double value)`<br>Writes a `double` to the stream message.                                                             |
    | `void`             | `writeFloat``(float value)`<br>Writes a `float` to the stream message.                                                                |
    | `void`             | `writeInt``(int value)`<br>Writes an `int` to the stream message.                                                                     |
    | `void`             | `writeLong``(long value)`<br>Writes a `long` to the stream message.                                                                   |
    | `void`             | `writeObject``(java.lang.Object value)`<br>Writes an object to the stream message.                                                    |
    | `void`             | `writeShort``(short value)`<br>Writes a `short` to the stream message.                                                                |
    | `void`             | `writeString``(java.lang.String value)`<br>Writes a `String` to the stream message.                                                   |

    - ### Methods inherited from interface javax.jms.[Message](Message.md)

      [`acknowledge`](Message.md)`, `[`clearBody`](Message.md)`, `[`clearProperties`](Message.md)`, `[`getBooleanProperty`](Message.md)`, `[`getByteProperty`](Message.md)`, `[`getDoubleProperty`](Message.md)`, `[`getFloatProperty`](Message.md)`, `[`getIntProperty`](Message.md)`, `[`getJMSCorrelationID`](Message.md)`, `[`getJMSCorrelationIDAsBytes`](Message.md)`, `[`getJMSDeliveryMode`](Message.md)`, `[`getJMSDestination`](Message.md)`, `[`getJMSExpiration`](Message.md)`, `[`getJMSMessageID`](Message.md)`, `[`getJMSPriority`](Message.md)`, `[`getJMSRedelivered`](Message.md)`, `[`getJMSReplyTo`](Message.md)`, `[`getJMSTimestamp`](Message.md)`, `[`getJMSType`](Message.md)`, `[`getLongProperty`](Message.md)`, `[`getObjectProperty`](Message.md)`, `[`getPropertyNames`](Message.md)`, `[`getShortProperty`](Message.md)`, `[`getStringProperty`](Message.md)`, `[`propertyExists`](Message.md)`, `[`setBooleanProperty`](Message.md)`, `[`setByteProperty`](Message.md)`, `[`setDoubleProperty`](Message.md)`, `[`setFloatProperty`](Message.md)`, `[`setIntProperty`](Message.md)`, `[`setJMSCorrelationID`](Message.md)`, `[`setJMSCorrelationIDAsBytes`](Message.md)`, `[`setJMSDeliveryMode`](Message.md)`, `[`setJMSDestination`](Message.md)`, `[`setJMSExpiration`](Message.md)`, `[`setJMSMessageID`](Message.md)`, `[`setJMSPriority`](Message.md)`, `[`setJMSRedelivered`](Message.md)`, `[`setJMSReplyTo`](Message.md)`, `[`setJMSTimestamp`](Message.md)`, `[`setJMSType`](Message.md)`, `[`setLongProperty`](Message.md)`, `[`setObjectProperty`](Message.md)`, `[`setShortProperty`](Message.md)`, `[`setStringProperty`](Message.md)

<!-- -->

- - ### Method Detail

    - #### readBoolean

          boolean readBoolean()
                       throws JMSException

      Reads a `boolean` from the stream message.
      Returns:
      the `boolean` value read

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readByte

          byte readByte()
                 throws JMSException

      Reads a `byte` value from the stream message.
      Returns:
      the next byte from the stream message as a 8-bit `byte`

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readShort

          short readShort()
                   throws JMSException

      Reads a 16-bit integer from the stream message.
      Returns:
      a 16-bit integer from the stream message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readChar

          char readChar()
                 throws JMSException

      Reads a Unicode character value from the stream message.
      Returns:
      a Unicode character from the stream message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readInt

          int readInt()
               throws JMSException

      Reads a 32-bit integer from the stream message.
      Returns:
      a 32-bit integer value from the stream message, interpreted as an `int`

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readLong

          long readLong()
                 throws JMSException

      Reads a 64-bit integer from the stream message.
      Returns:
      a 64-bit integer value from the stream message, interpreted as a `long`

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readFloat

          float readFloat()
                   throws JMSException

      Reads a `float` from the stream message.
      Returns:
      a `float` value from the stream message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readDouble

          double readDouble()
                     throws JMSException

      Reads a `double` from the stream message.
      Returns:
      a `double` value from the stream message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readString

          java.lang.String readString()
                               throws JMSException

      Reads a `String` from the stream message.
      Returns:
      a Unicode string from the stream message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readBytes

          int readBytes(byte[] value)
                 throws JMSException

      Reads a byte array field from the stream message into the specified `byte[]` object (the read buffer).
      To read the field value, `readBytes` should be successively called until it returns a value less than the length of the read buffer. The value of the bytes in the buffer following the last byte read is undefined.

      If `readBytes` returns a value equal to the length of the buffer, a subsequent `readBytes` call must be made. If there are no more bytes to be read, this call returns -1.

      If the byte array field value is null, `readBytes` returns -1.

      If the byte array field value is empty, `readBytes` returns 0.

      Once the first `readBytes` call on a `byte[]` field value has been made, the full value of the field must be read before it is valid to read the next field. An attempt to read the next field before that has been done will throw a `MessageFormatException`.

      To read the byte field value into a new `byte[]` object, use the `readObject` method.

      Parameters:
      `value` - the buffer into which the data is read

      Returns:
      the total number of bytes read into the buffer, or -1 if there is no more data because the end of the byte field has been reached

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

      See Also:
      `StreamMessage.readObject()`

    <!-- -->

    - #### readObject

          java.lang.Object readObject()
                               throws JMSException

      Reads an object from the stream message.
      This method can be used to return, in objectified format, an object in the Java programming language ("Java object") that has been written to the stream with the equivalent `writeObject` method call, or its equivalent primitive `write`*`type`* method.

      Note that byte values are returned as `byte[]`, not `Byte[]`.

      An attempt to call `readObject` to read a byte field value into a new `byte[]` object before the full value of the byte field has been read will throw a `MessageFormatException`.

      Returns:
      a Java object from the stream message, in objectified format (for example, if the object was written as an `int`, an `Integer` is returned)

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of message stream has been reached.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

      See Also:
      `StreamMessage.readBytes(byte[] value)`

    <!-- -->

    - #### writeBoolean

          void writeBoolean(boolean value)
                     throws JMSException

      Writes a `boolean` to the stream message. The value `true` is written as the value `(byte)1`; the value `false` is written as the value `(byte)0`.
      Parameters:
      `value` - the `boolean` value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeByte

          void writeByte(byte value)
                  throws JMSException

      Writes a `byte` to the stream message.
      Parameters:
      `value` - the `byte` value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeShort

          void writeShort(short value)
                   throws JMSException

      Writes a `short` to the stream message.
      Parameters:
      `value` - the `short` value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeChar

          void writeChar(char value)
                  throws JMSException

      Writes a `char` to the stream message.
      Parameters:
      `value` - the `char` value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeInt

          void writeInt(int value)
                 throws JMSException

      Writes an `int` to the stream message.
      Parameters:
      `value` - the `int` value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeLong

          void writeLong(long value)
                  throws JMSException

      Writes a `long` to the stream message.
      Parameters:
      `value` - the `long` value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeFloat

          void writeFloat(float value)
                   throws JMSException

      Writes a `float` to the stream message.
      Parameters:
      `value` - the `float` value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeDouble

          void writeDouble(double value)
                    throws JMSException

      Writes a `double` to the stream message.
      Parameters:
      `value` - the `double` value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeString

          void writeString(java.lang.String value)
                    throws JMSException

      Writes a `String` to the stream message.
      Parameters:
      `value` - the `String` value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeBytes

          void writeBytes(byte[] value)
                   throws JMSException

      Writes a byte array field to the stream message.
      The byte array `value` is written to the message as a byte array field. Consecutively written byte array fields are treated as two distinct fields when the fields are read.

      Parameters:
      `value` - the byte array value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeBytes

          void writeBytes(byte[] value,
                          int offset,
                          int length)
                   throws JMSException

      Writes a portion of a byte array as a byte array field to the stream message.
      The a portion of the byte array `value` is written to the message as a byte array field. Consecutively written byte array fields are treated as two distinct fields when the fields are read.

      Parameters:
      `value` - the byte array value to be written

      `offset` - the initial offset within the byte array

      `length` - the number of bytes to use

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeObject

          void writeObject(java.lang.Object value)
                    throws JMSException

      Writes an object to the stream message.
      This method works only for the objectified primitive object types (`Integer`, `Double`, `Long` ...), `String` objects, and byte arrays.

      Parameters:
      `value` - the Java object to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if the object is invalid.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### reset

          void reset()
              throws JMSException

      Puts the message body in read-only mode and repositions the stream to the beginning.
      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to reset the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if the message has an invalid format.

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

- [Prev Class](Session.md)
- [Next Class](TemporaryQueue.md)

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
