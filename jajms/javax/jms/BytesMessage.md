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

- Prev Class
- [Next Class](Connection.md)

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

## Interface BytesMessage

- All Superinterfaces:
  [Message](Message.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsBytesMessage](../../oracle/jms/AQjmsBytesMessage.md)

  ------------------------------------------------------------------------



      public interface BytesMessage
      extends Message

  A `BytesMessage` object is used to send a message containing a stream of uninterpreted bytes. It inherits from the `Message` interface and adds a bytes message body. The receiver of the message supplies the interpretation of the bytes.
  The `BytesMessage` methods are based largely on those found in `java.io.DataInputStream` and `java.io.DataOutputStream`.

  This message type is for client encoding of existing message formats. If possible, one of the other self-defining message types should be used instead.

  Although the JMS API allows the use of message properties with byte messages, they are typically not used, since the inclusion of properties may affect the format.

  The primitive types can be written explicitly using methods for each type. They may also be written generically as objects. For instance, a call to `BytesMessage.writeInt(6)` is equivalent to `BytesMessage.writeObject(new Integer(6))`. Both forms are provided, because the explicit form is convenient for static programming, and the object form is needed when types are not known at compile time.

  When the message is first created, and when `clearBody` is called, the body of the message is in write-only mode. After the first call to `reset` has been made, the message body is in read-only mode. After a message has been sent, the client that sent it can retain and modify it without affecting the message that has been sent. The same message object can be sent multiple times. When a message has been received, the provider has called `reset` so that the message body is in read-only mode for the client.

  If `clearBody` is called on a message in read-only mode, the message body is cleared and the message is in write-only mode.

  If a client attempts to read a message in write-only mode, a `MessageNotReadableException` is thrown.

  If a client attempts to write a message in read-only mode, a `MessageNotWriteableException` is thrown.

  See Also:
  [`Session.createBytesMessage()`](Session.md), [`MapMessage`](MapMessage.md), [`Message`](Message.md), [`ObjectMessage`](ObjectMessage.md), [`StreamMessage`](StreamMessage.md), [`TextMessage`](TextMessage.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Message](Message.md)

      [`DEFAULT_DELIVERY_MODE`](Message.md)`, `[`DEFAULT_PRIORITY`](Message.md)`, `[`DEFAULT_TIME_TO_LIVE`](Message.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                                   |
    |--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `long`             | `getBodyLength``()`<br>Gets the number of bytes of the message body when the message is in read-only mode.                                                                                                                               |
    | `boolean`          | `readBoolean``()`<br>Reads a `boolean` from the bytes message stream.                                                                                                                                                                    |
    | `byte`             | `readByte``()`<br>Reads a signed 8-bit value from the bytes message stream.                                                                                                                                                              |
    | `int`              | `readBytes``(byte[] value)`<br>Reads a byte array from the bytes message stream.                                                                                                                                                         |
    | `int`              | `readBytes``(byte[] value, int length)`<br>Reads a portion of the bytes message stream.                                                                                                                                                  |
    | `char`             | `readChar``()`<br>Reads a Unicode character value from the bytes message stream.                                                                                                                                                         |
    | `double`           | `readDouble``()`<br>Reads a `double` from the bytes message stream.                                                                                                                                                                      |
    | `float`            | `readFloat``()`<br>Reads a `float` from the bytes message stream.                                                                                                                                                                        |
    | `int`              | `readInt``()`<br>Reads a signed 32-bit integer from the bytes message stream.                                                                                                                                                            |
    | `long`             | `readLong``()`<br>Reads a signed 64-bit integer from the bytes message stream.                                                                                                                                                           |
    | `short`            | `readShort``()`<br>Reads a signed 16-bit number from the bytes message stream.                                                                                                                                                           |
    | `int`              | `readUnsignedByte``()`<br>Reads an unsigned 8-bit number from the bytes message stream.                                                                                                                                                  |
    | `int`              | `readUnsignedShort``()`<br>Reads an unsigned 16-bit number from the bytes message stream.                                                                                                                                                |
    | `java.lang.String` | `readUTF``()`<br>Reads a string that has been encoded using a modified UTF-8 format from the bytes message stream.                                                                                                                       |
    | `void`             | `reset``()`<br>Puts the message body in read-only mode and repositions the stream of bytes to the beginning.                                                                                                                             |
    | `void`             | `writeBoolean``(boolean value)`<br>Writes a `boolean` to the bytes message stream as a 1-byte value.                                                                                                                                     |
    | `void`             | `writeByte``(byte value)`<br>Writes a `byte` to the bytes message stream as a 1-byte value.                                                                                                                                              |
    | `void`             | `writeBytes``(byte[] value)`<br>Writes a byte array to the bytes message stream.                                                                                                                                                         |
    | `void`             | `writeBytes``(byte[] value, int offset, int length)`<br>Writes a portion of a byte array to the bytes message stream.                                                                                                                    |
    | `void`             | `writeChar``(char value)`<br>Writes a `char` to the bytes message stream as a 2-byte value, high byte first.                                                                                                                             |
    | `void`             | `writeDouble``(double value)`<br>Converts the `double` argument to a `long` using the `doubleToLongBits` method in class `Double`, and then writes that `long` value to the bytes message stream as an 8-byte quantity, high byte first. |
    | `void`             | `writeFloat``(float value)`<br>Converts the `float` argument to an `int` using the `floatToIntBits` method in class `Float`, and then writes that `int` value to the bytes message stream as a 4-byte quantity, high byte first.         |
    | `void`             | `writeInt``(int value)`<br>Writes an `int` to the bytes message stream as four bytes, high byte first.                                                                                                                                   |
    | `void`             | `writeLong``(long value)`<br>Writes a `long` to the bytes message stream as eight bytes, high byte first.                                                                                                                                |
    | `void`             | `writeObject``(java.lang.Object value)`<br>Writes an object to the bytes message stream.                                                                                                                                                 |
    | `void`             | `writeShort``(short value)`<br>Writes a `short` to the bytes message stream as two bytes, high byte first.                                                                                                                               |
    | `void`             | `writeUTF``(java.lang.String value)`<br>Writes a string to the bytes message stream using UTF-8 encoding in a machine-independent manner.                                                                                                |

    - ### Methods inherited from interface javax.jms.[Message](Message.md)

      [`acknowledge`](Message.md)`, `[`clearBody`](Message.md)`, `[`clearProperties`](Message.md)`, `[`getBooleanProperty`](Message.md)`, `[`getByteProperty`](Message.md)`, `[`getDoubleProperty`](Message.md)`, `[`getFloatProperty`](Message.md)`, `[`getIntProperty`](Message.md)`, `[`getJMSCorrelationID`](Message.md)`, `[`getJMSCorrelationIDAsBytes`](Message.md)`, `[`getJMSDeliveryMode`](Message.md)`, `[`getJMSDestination`](Message.md)`, `[`getJMSExpiration`](Message.md)`, `[`getJMSMessageID`](Message.md)`, `[`getJMSPriority`](Message.md)`, `[`getJMSRedelivered`](Message.md)`, `[`getJMSReplyTo`](Message.md)`, `[`getJMSTimestamp`](Message.md)`, `[`getJMSType`](Message.md)`, `[`getLongProperty`](Message.md)`, `[`getObjectProperty`](Message.md)`, `[`getPropertyNames`](Message.md)`, `[`getShortProperty`](Message.md)`, `[`getStringProperty`](Message.md)`, `[`propertyExists`](Message.md)`, `[`setBooleanProperty`](Message.md)`, `[`setByteProperty`](Message.md)`, `[`setDoubleProperty`](Message.md)`, `[`setFloatProperty`](Message.md)`, `[`setIntProperty`](Message.md)`, `[`setJMSCorrelationID`](Message.md)`, `[`setJMSCorrelationIDAsBytes`](Message.md)`, `[`setJMSDeliveryMode`](Message.md)`, `[`setJMSDestination`](Message.md)`, `[`setJMSExpiration`](Message.md)`, `[`setJMSMessageID`](Message.md)`, `[`setJMSPriority`](Message.md)`, `[`setJMSRedelivered`](Message.md)`, `[`setJMSReplyTo`](Message.md)`, `[`setJMSTimestamp`](Message.md)`, `[`setJMSType`](Message.md)`, `[`setLongProperty`](Message.md)`, `[`setObjectProperty`](Message.md)`, `[`setShortProperty`](Message.md)`, `[`setStringProperty`](Message.md)

<!-- -->

- - ### Method Detail

    - #### getBodyLength

          long getBodyLength()
                      throws JMSException

      Gets the number of bytes of the message body when the message is in read-only mode. The value returned can be used to allocate a byte array. The value returned is the entire length of the message body, regardless of where the pointer for reading the message is currently located.
      Returns:
      number of bytes in the message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

      Since:
      1.1

    <!-- -->

    - #### readBoolean

          boolean readBoolean()
                       throws JMSException

      Reads a `boolean` from the bytes message stream.
      Returns:
      the `boolean` value read

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readByte

          byte readByte()
                 throws JMSException

      Reads a signed 8-bit value from the bytes message stream.
      Returns:
      the next byte from the bytes message stream as a signed 8-bit `byte`

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readUnsignedByte

          int readUnsignedByte()
                        throws JMSException

      Reads an unsigned 8-bit number from the bytes message stream.
      Returns:
      the next byte from the bytes message stream, interpreted as an unsigned 8-bit number

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readShort

          short readShort()
                   throws JMSException

      Reads a signed 16-bit number from the bytes message stream.
      Returns:
      the next two bytes from the bytes message stream, interpreted as a signed 16-bit number

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readUnsignedShort

          int readUnsignedShort()
                         throws JMSException

      Reads an unsigned 16-bit number from the bytes message stream.
      Returns:
      the next two bytes from the bytes message stream, interpreted as an unsigned 16-bit integer

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readChar

          char readChar()
                 throws JMSException

      Reads a Unicode character value from the bytes message stream.
      Returns:
      the next two bytes from the bytes message stream as a Unicode character

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readInt

          int readInt()
               throws JMSException

      Reads a signed 32-bit integer from the bytes message stream.
      Returns:
      the next four bytes from the bytes message stream, interpreted as an `int`

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readLong

          long readLong()
                 throws JMSException

      Reads a signed 64-bit integer from the bytes message stream.
      Returns:
      the next eight bytes from the bytes message stream, interpreted as a `long`

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readFloat

          float readFloat()
                   throws JMSException

      Reads a `float` from the bytes message stream.
      Returns:
      the next four bytes from the bytes message stream, interpreted as a `float`

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readDouble

          double readDouble()
                     throws JMSException

      Reads a `double` from the bytes message stream.
      Returns:
      the next eight bytes from the bytes message stream, interpreted as a `double`

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readUTF

          java.lang.String readUTF()
                            throws JMSException

      Reads a string that has been encoded using a modified UTF-8 format from the bytes message stream.
      For more information on the UTF-8 format, see "File System Safe UCS Transformation Format (FSS_UTF)", X/Open Preliminary Specification, X/Open Company Ltd., Document Number: P316. This information also appears in ISO/IEC 10646, Annex P.

      Returns:
      a Unicode string from the bytes message stream

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readBytes

          int readBytes(byte[] value)
                 throws JMSException

      Reads a byte array from the bytes message stream.
      If the length of array `value` is less than the number of bytes remaining to be read from the stream, the array should be filled. A subsequent call reads the next increment, and so on.

      If the number of bytes remaining in the stream is less than the length of array `value`, the bytes should be read into the array. The return value of the total number of bytes read will be less than the length of the array, indicating that there are no more bytes left to be read from the stream. The next read of the stream returns -1.

      Parameters:
      `value` - the buffer into which the data is read

      Returns:
      the total number of bytes read into the buffer, or -1 if there is no more data because the end of the stream has been reached

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readBytes

          int readBytes(byte[] value,
                        int length)
                 throws JMSException

      Reads a portion of the bytes message stream.
      If the length of array `value` is less than the number of bytes remaining to be read from the stream, the array should be filled. A subsequent call reads the next increment, and so on.

      If the number of bytes remaining in the stream is less than the length of array `value`, the bytes should be read into the array. The return value of the total number of bytes read will be less than the length of the array, indicating that there are no more bytes left to be read from the stream. The next read of the stream returns -1.

      If `length` is negative, or `length` is greater than the length of the array `value`, then an `IndexOutOfBoundsException` is thrown. No bytes will be read from the stream for this exception case.

      Parameters:
      `value` - the buffer into which the data is read

      `length` - the number of bytes to read; must be less than or equal to `value.length`

      Returns:
      the total number of bytes read into the buffer, or -1 if there is no more data because the end of the stream has been reached

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageNotReadableException`](MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### writeBoolean

          void writeBoolean(boolean value)
                     throws JMSException

      Writes a `boolean` to the bytes message stream as a 1-byte value. The value `true` is written as the value `(byte)1`; the value `false` is written as the value `(byte)0`.
      Parameters:
      `value` - the `boolean` value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeByte

          void writeByte(byte value)
                  throws JMSException

      Writes a `byte` to the bytes message stream as a 1-byte value.
      Parameters:
      `value` - the `byte` value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeShort

          void writeShort(short value)
                   throws JMSException

      Writes a `short` to the bytes message stream as two bytes, high byte first.
      Parameters:
      `value` - the `short` to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeChar

          void writeChar(char value)
                  throws JMSException

      Writes a `char` to the bytes message stream as a 2-byte value, high byte first.
      Parameters:
      `value` - the `char` value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeInt

          void writeInt(int value)
                 throws JMSException

      Writes an `int` to the bytes message stream as four bytes, high byte first.
      Parameters:
      `value` - the `int` to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeLong

          void writeLong(long value)
                  throws JMSException

      Writes a `long` to the bytes message stream as eight bytes, high byte first.
      Parameters:
      `value` - the `long` to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeFloat

          void writeFloat(float value)
                   throws JMSException

      Converts the `float` argument to an `int` using the `floatToIntBits` method in class `Float`, and then writes that `int` value to the bytes message stream as a 4-byte quantity, high byte first.
      Parameters:
      `value` - the `float` value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeDouble

          void writeDouble(double value)
                    throws JMSException

      Converts the `double` argument to a `long` using the `doubleToLongBits` method in class `Double`, and then writes that `long` value to the bytes message stream as an 8-byte quantity, high byte first.
      Parameters:
      `value` - the `double` value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeUTF

          void writeUTF(java.lang.String value)
                 throws JMSException

      Writes a string to the bytes message stream using UTF-8 encoding in a machine-independent manner.
      For more information on the UTF-8 format, see "File System Safe UCS Transformation Format (FSS_UTF)", X/Open Preliminary Specification, X/Open Company Ltd., Document Number: P316. This information also appears in ISO/IEC 10646, Annex P.

      Parameters:
      `value` - the `String` value to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeBytes

          void writeBytes(byte[] value)
                   throws JMSException

      Writes a byte array to the bytes message stream.
      Parameters:
      `value` - the byte array to be written

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeBytes

          void writeBytes(byte[] value,
                          int offset,
                          int length)
                   throws JMSException

      Writes a portion of a byte array to the bytes message stream.
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

      Writes an object to the bytes message stream.
      This method works only for the objectified primitive object types (`Integer`, `Double`, `Long` ...), `String` objects, and byte arrays.

      Parameters:
      `value` - the object in the Java programming language ("Java object") to be written; it must not be null

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if the object is of an invalid type.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

      `java.lang.NullPointerException` - if the parameter `value` is null.

    <!-- -->

    - #### reset

          void reset()
              throws JMSException

      Puts the message body in read-only mode and repositions the stream of bytes to the beginning.
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

- Prev Class
- [Next Class](Connection.md)

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
