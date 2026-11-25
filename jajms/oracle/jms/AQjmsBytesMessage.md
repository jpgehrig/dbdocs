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

- [Prev Class](AQjmsAdtMessage.md)
- [Next Class](AQjmsConnection.md)

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

## Class AQjmsBytesMessage

- java.lang.Object

- - [oracle.jms.AQjmsMessage](AQjmsMessage.md)

  - - oracle.jms.AQjmsBytesMessage

<!-- -->

- All Implemented Interfaces:
  [BytesMessage](../../javax/jms/BytesMessage.md), [Message](../../javax/jms/Message.md)

  ------------------------------------------------------------------------



      public class AQjmsBytesMessage
      extends AQjmsMessage
      implements BytesMessage

  This is an Oracle class which implements `javax.jms.BytesMessage`.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Message](../../javax/jms/Message.md)

      [`DEFAULT_DELIVERY_MODE`](../../javax/jms/Message.md)`, `[`DEFAULT_PRIORITY`](../../javax/jms/Message.md)`, `[`DEFAULT_TIME_TO_LIVE`](../../javax/jms/Message.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type      | Method and Description                                                                                                                                                                                                                   |
    |------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                 | `clearBody``()`<br>Clears out the message body.                                                                                                                                                                                          |
    | `java.io.OutputStream` | `getBody``(java.io.OutputStream outputStream)`<br>Writes the message body to the OutputStream specified.                                                                                                                                 |
    | `java.io.OutputStream` | `getBody``(java.io.OutputStream outputStream, int chunkSize)`<br>Writes the message body to the OutputStream specified, with chunkSize bytes written at a time.                                                                          |
    | `java.io.OutputStream` | `getBody``(java.io.OutputStream outputStream, int chunkSize, long timeout)`<br>Writes the message body to the OutputStream specified, chunkSize bytes at a time.                                                                         |
    | `java.io.OutputStream` | `getBody``(java.io.OutputStream outputStream, long timeout)`<br>Writes the message body to the OutputStream specified.                                                                                                                   |
    | `long`                 | `getBodyLength``()`<br>Gets the number of bytes of the message body when the message is in read-only mode.                                                                                                                               |
    | `boolean`              | `readBoolean``()`<br>Reads a `boolean` from the bytes message stream.                                                                                                                                                                    |
    | `byte`                 | `readByte``()`<br>Reads a signed 8-bit value from the bytes message stream.                                                                                                                                                              |
    | `int`                  | `readBytes``(byte[] value)`<br>Reads a byte array from the bytes message stream.                                                                                                                                                         |
    | `int`                  | `readBytes``(byte[] value, int length)`<br>Reads a portion of the bytes message stream.                                                                                                                                                  |
    | `char`                 | `readChar``()`<br>Reads a Unicode character value from the bytes message stream.                                                                                                                                                         |
    | `double`               | `readDouble``()`<br>Reads a `double` from the bytes message stream.                                                                                                                                                                      |
    | `float`                | `readFloat``()`<br>Reads a `float` from the bytes message stream.                                                                                                                                                                        |
    | `int`                  | `readInt``()`<br>Reads a signed 32-bit integer from the bytes message stream.                                                                                                                                                            |
    | `long`                 | `readLong``()`<br>Reads a signed 64-bit integer from the bytes message stream.                                                                                                                                                           |
    | `short`                | `readShort``()`<br>Reads a signed 16-bit number from the bytes message stream.                                                                                                                                                           |
    | `int`                  | `readUnsignedByte``()`<br>Reads an unsigned 8-bit number from the bytes message stream.                                                                                                                                                  |
    | `int`                  | `readUnsignedShort``()`<br>Reads an unsigned 16-bit number from the bytes message stream.                                                                                                                                                |
    | `java.lang.String`     | `readUTF``()`<br>Reads a string that has been encoded using a modified UTF-8 format from the bytes message stream.                                                                                                                       |
    | `void`                 | `reset``()`<br>Puts the message body in read-only mode and repositions the stream of bytes to the beginning.                                                                                                                             |
    | `void`                 | `setInputStream``(java.io.InputStream inputStream)`<br>Writes an InputStream to the bytes message stream                                                                                                                                 |
    | `void`                 | `writeBoolean``(boolean value)`<br>Writes a `boolean` to the bytes message stream as a 1-byte value.                                                                                                                                     |
    | `void`                 | `writeByte``(byte value)`<br>Writes a `byte` to the bytes message stream as a 1-byte value.                                                                                                                                              |
    | `void`                 | `writeBytes``(byte[] value)`<br>Writes a byte array to the bytes message stream.                                                                                                                                                         |
    | `void`                 | `writeBytes``(byte[] value, int offset, int length)`<br>Writes a portion of a byte array to the bytes message stream.                                                                                                                    |
    | `void`                 | `writeChar``(char value)`<br>Writes a `char` to the bytes message stream as a 2-byte value, high byte first.                                                                                                                             |
    | `void`                 | `writeDouble``(double value)`<br>Converts the `double` argument to a `long` using the `doubleToLongBits` method in class `Double`, and then writes that `long` value to the bytes message stream as an 8-byte quantity, high byte first. |
    | `void`                 | `writeFloat``(float value)`<br>Converts the `float` argument to an `int` using the `floatToIntBits` method in class `Float`, and then writes that `int` value to the bytes message stream as a 4-byte quantity, high byte first.         |
    | `void`                 | `writeInt``(int value)`<br>Writes an `int` to the bytes message stream as four bytes, high byte first.                                                                                                                                   |
    | `void`                 | `writeLong``(long value)`<br>Writes a `long` to the bytes message stream as eight bytes, high byte first.                                                                                                                                |
    | `void`                 | `writeObject``(java.lang.Object value)`<br>Writes an object to the bytes message stream.                                                                                                                                                 |
    | `void`                 | `writeShort``(short value)`<br>Writes a `short` to the bytes message stream as two bytes, high byte first.                                                                                                                               |
    | `void`                 | `writeUTF``(java.lang.String value)`<br>Writes a string to the bytes message stream using UTF-8 encoding in a machine-independent manner.                                                                                                |

    - ### Methods inherited from class oracle.jms.[AQjmsMessage](AQjmsMessage.md)

      [`acknowledge`](AQjmsMessage.md)`, `[`clearProperties`](AQjmsMessage.md)`, `[`getAttempts`](AQjmsMessage.md)`, `[`getBooleanProperty`](AQjmsMessage.md)`, `[`getByteProperty`](AQjmsMessage.md)`, `[`getDoubleProperty`](AQjmsMessage.md)`, `[`getFloatProperty`](AQjmsMessage.md)`, `[`getIntProperty`](AQjmsMessage.md)`, `[`getJMSCorrelationID`](AQjmsMessage.md)`, `[`getJMSCorrelationIDAsBytes`](AQjmsMessage.md)`, `[`getJMSDeliveryMode`](AQjmsMessage.md)`, `[`getJMSDestination`](AQjmsMessage.md)`, `[`getJMSExpiration`](AQjmsMessage.md)`, `[`getJMSMessageID`](AQjmsMessage.md)`, `[`getJMSMessageIDAsBytes`](AQjmsMessage.md)`, `[`getJMSPriority`](AQjmsMessage.md)`, `[`getJMSRedelivered`](AQjmsMessage.md)`, `[`getJMSReplyTo`](AQjmsMessage.md)`, `[`getJMSTimestamp`](AQjmsMessage.md)`, `[`getJMSType`](AQjmsMessage.md)`, `[`getLongProperty`](AQjmsMessage.md)`, `[`getObjectProperty`](AQjmsMessage.md)`, `[`getPropertyNames`](AQjmsMessage.md)`, `[`getSenderID`](AQjmsMessage.md)`, `[`getShortProperty`](AQjmsMessage.md)`, `[`getStringProperty`](AQjmsMessage.md)`, `[`getUserPropertyNames`](AQjmsMessage.md)`, `[`isLargeBody`](AQjmsMessage.md)`, `[`propertyExists`](AQjmsMessage.md)`, `[`setBooleanProperty`](AQjmsMessage.md)`, `[`setByteProperty`](AQjmsMessage.md)`, `[`setDoubleProperty`](AQjmsMessage.md)`, `[`setFloatProperty`](AQjmsMessage.md)`, `[`setIntProperty`](AQjmsMessage.md)`, `[`setJMSCorrelationID`](AQjmsMessage.md)`, `[`setJMSCorrelationIDAsBytes`](AQjmsMessage.md)`, `[`setJMSDeliveryMode`](AQjmsMessage.md)`, `[`setJMSDestination`](AQjmsMessage.md)`, `[`setJMSExpiration`](AQjmsMessage.md)`, `[`setJMSMessageID`](AQjmsMessage.md)`, `[`setJMSPriority`](AQjmsMessage.md)`, `[`setJMSRedelivered`](AQjmsMessage.md)`, `[`setJMSReplyTo`](AQjmsMessage.md)`, `[`setJMSTimestamp`](AQjmsMessage.md)`, `[`setJMSType`](AQjmsMessage.md)`, `[`setLongProperty`](AQjmsMessage.md)`, `[`setObjectProperty`](AQjmsMessage.md)`, `[`setSenderID`](AQjmsMessage.md)`, `[`setShortProperty`](AQjmsMessage.md)`, `[`setStringProperty`](AQjmsMessage.md)`, `[`test_getUserProperties`](AQjmsMessage.md)

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

      Reads a `boolean` from the bytes message stream.
      Specified by:
      [`readBoolean`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Returns:
      the `boolean` value read

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readByte

          public byte readByte()
                        throws JMSException

      Reads a signed 8-bit value from the bytes message stream.
      Specified by:
      [`readByte`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Returns:
      the next byte from the bytes message stream as a signed 8-bit `byte`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readUnsignedByte

          public int readUnsignedByte()
                               throws JMSException

      Reads an unsigned 8-bit number from the bytes message stream.
      Specified by:
      [`readUnsignedByte`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Returns:
      the next byte from the bytes message stream, interpreted as an unsigned 8-bit number

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readShort

          public short readShort()
                          throws JMSException

      Reads a signed 16-bit number from the bytes message stream.
      Specified by:
      [`readShort`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Returns:
      the next two bytes from the bytes message stream, interpreted as a signed 16-bit number

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readUnsignedShort

          public int readUnsignedShort()
                                throws JMSException

      Reads an unsigned 16-bit number from the bytes message stream.
      Specified by:
      [`readUnsignedShort`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Returns:
      the next two bytes from the bytes message stream, interpreted as an unsigned 16-bit integer

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readChar

          public char readChar()
                        throws JMSException

      Reads a Unicode character value from the bytes message stream.
      Specified by:
      [`readChar`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Returns:
      the next two bytes from the bytes message stream as a Unicode character

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readInt

          public int readInt()
                      throws JMSException

      Reads a signed 32-bit integer from the bytes message stream.
      Specified by:
      [`readInt`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Returns:
      the next four bytes from the bytes message stream, interpreted as an `int`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readLong

          public long readLong()
                        throws JMSException

      Reads a signed 64-bit integer from the bytes message stream.
      Specified by:
      [`readLong`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Returns:
      the next eight bytes from the bytes message stream, interpreted as a `long`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readFloat

          public float readFloat()
                          throws JMSException

      Reads a `float` from the bytes message stream.
      Specified by:
      [`readFloat`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Returns:
      the next four bytes from the bytes message stream, interpreted as a `float`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readDouble

          public double readDouble()
                            throws JMSException

      Reads a `double` from the bytes message stream.
      Specified by:
      [`readDouble`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Returns:
      the next eight bytes from the bytes message stream, interpreted as a `double`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readUTF

          public java.lang.String readUTF()
                                   throws JMSException

      Reads a string that has been encoded using a modified UTF-8 format from the bytes message stream.
      For more information on the UTF-8 format, see "File System Safe UCS Transformation Format (FSS_UTF)", X/Open Preliminary Specification, X/Open Company Ltd., Document Number: P316. This information also appears in ISO/IEC 10646, Annex P.

      Specified by:
      [`readUTF`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Returns:
      a Unicode string from the bytes message stream

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageEOFException`](../../javax/jms/MessageEOFException.md) - if unexpected end of bytes stream has been reached.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readBytes

          public int readBytes(byte[] value)
                        throws JMSException

      Reads a byte array from the bytes message stream.
      If the length of array `value` is less than the number of bytes remaining to be read from the stream, the array should be filled. A subsequent call reads the next increment, and so on.

      If the number of bytes remaining in the stream is less than the length of array `value`, the bytes should be read into the array. The return value of the total number of bytes read will be less than the length of the array, indicating that there are no more bytes left to be read from the stream. The next read of the stream returns -1.

      Specified by:
      [`readBytes`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Parameters:
      `value` - the buffer into which the data is read

      Returns:
      the total number of bytes read into the buffer, or -1 if there is no more data because the end of the stream has been reached

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### readBytes

          public int readBytes(byte[] value,
                               int length)
                        throws JMSException

      Reads a portion of the bytes message stream.
      If the length of array `value` is less than the number of bytes remaining to be read from the stream, the array should be filled. A subsequent call reads the next increment, and so on.

      If the number of bytes remaining in the stream is less than the length of array `value`, the bytes should be read into the array. The return value of the total number of bytes read will be less than the length of the array, indicating that there are no more bytes left to be read from the stream. The next read of the stream returns -1.

      If `length` is negative, or `length` is greater than the length of the array `value`, then an `IndexOutOfBoundsException` is thrown. No bytes will be read from the stream for this exception case.

      Specified by:
      [`readBytes`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Parameters:
      `value` - the buffer into which the data is read

      `length` - the number of bytes to read; must be less than or equal to `value.length`

      Returns:
      the total number of bytes read into the buffer, or -1 if there is no more data because the end of the stream has been reached

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

    <!-- -->

    - #### writeBoolean

          public void writeBoolean(boolean value)
                            throws JMSException

      Writes a `boolean` to the bytes message stream as a 1-byte value. The value `true` is written as the value `(byte)1`; the value `false` is written as the value `(byte)0`.
      Specified by:
      [`writeBoolean`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Parameters:
      `value` - the `boolean` value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeByte

          public void writeByte(byte value)
                         throws JMSException

      Writes a `byte` to the bytes message stream as a 1-byte value.
      Specified by:
      [`writeByte`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Parameters:
      `value` - the `byte` value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeShort

          public void writeShort(short value)
                          throws JMSException

      Writes a `short` to the bytes message stream as two bytes, high byte first.
      Specified by:
      [`writeShort`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Parameters:
      `value` - the `short` to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeChar

          public void writeChar(char value)
                         throws JMSException

      Writes a `char` to the bytes message stream as a 2-byte value, high byte first.
      Specified by:
      [`writeChar`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Parameters:
      `value` - the `char` value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeInt

          public void writeInt(int value)
                        throws JMSException

      Writes an `int` to the bytes message stream as four bytes, high byte first.
      Specified by:
      [`writeInt`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Parameters:
      `value` - the `int` to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeLong

          public void writeLong(long value)
                         throws JMSException

      Writes a `long` to the bytes message stream as eight bytes, high byte first.
      Specified by:
      [`writeLong`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Parameters:
      `value` - the `long` to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeFloat

          public void writeFloat(float value)
                          throws JMSException

      Converts the `float` argument to an `int` using the `floatToIntBits` method in class `Float`, and then writes that `int` value to the bytes message stream as a 4-byte quantity, high byte first.
      Specified by:
      [`writeFloat`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Parameters:
      `value` - the `float` value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeDouble

          public void writeDouble(double value)
                           throws JMSException

      Converts the `double` argument to a `long` using the `doubleToLongBits` method in class `Double`, and then writes that `long` value to the bytes message stream as an 8-byte quantity, high byte first.
      Specified by:
      [`writeDouble`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Parameters:
      `value` - the `double` value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeUTF

          public void writeUTF(java.lang.String value)
                        throws JMSException

      Writes a string to the bytes message stream using UTF-8 encoding in a machine-independent manner.
      For more information on the UTF-8 format, see "File System Safe UCS Transformation Format (FSS_UTF)", X/Open Preliminary Specification, X/Open Company Ltd., Document Number: P316. This information also appears in ISO/IEC 10646, Annex P.

      Specified by:
      [`writeUTF`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Parameters:
      `value` - the `String` value to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeBytes

          public void writeBytes(byte[] value)
                          throws JMSException

      Writes a byte array to the bytes message stream.
      Specified by:
      [`writeBytes`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Parameters:
      `value` - the byte array to be written

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### writeBytes

          public void writeBytes(byte[] value,
                                 int offset,
                                 int length)
                          throws JMSException

      Writes a portion of a byte array to the bytes message stream.
      Specified by:
      [`writeBytes`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

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

      Writes an object to the bytes message stream.
      This method works only for the objectified primitive object types (`Integer`, `Double`, `Long` ...), `String` objects, and byte arrays.

      Specified by:
      [`writeObject`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Parameters:
      `value` - the object in the Java programming language ("Java object") to be written; it must not be null

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if the object is of an invalid type.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

      `java.lang.NullPointerException` - if the parameter `value` is null.

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

      Puts the message body in read-only mode and repositions the stream of bytes to the beginning.
      Specified by:
      [`reset`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to reset the message due to some internal error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if the message has an invalid format.

    <!-- -->

    - #### clearBody

          public void clearBody()
                         throws JMSException

      Description copied from class: [`AQjmsMessage`](AQjmsMessage.md)
      Clears out the message body. All other parts of the message are left untouched.
      Specified by:
      [`clearBody`](../../javax/jms/Message.md) in interface [`Message`](../../javax/jms/Message.md)

      Overrides:
      [`clearBody`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message body is not cleared due to some error.

    <!-- -->

    - #### getBodyLength

          public long getBodyLength()
                             throws JMSException

      Gets the number of bytes of the message body when the message is in read-only mode. The value returned can be used to allocate a byte array. The value returned is the entire length of the message body, regardless of where the pointer for reading the message is currently located.
      Specified by:
      [`getBodyLength`](../../javax/jms/BytesMessage.md) in interface [`BytesMessage`](../../javax/jms/BytesMessage.md)

      Overrides:
      [`getBodyLength`](AQjmsMessage.md) in class [`AQjmsMessage`](AQjmsMessage.md)

      Returns:
      number of bytes in the message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageNotReadableException`](../../javax/jms/MessageNotReadableException.md) - if the message is in write-only mode.

      Since:
      1.1

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

- [Prev Class](AQjmsAdtMessage.md)
- [Next Class](AQjmsConnection.md)

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
