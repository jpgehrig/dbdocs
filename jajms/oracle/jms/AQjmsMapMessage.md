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

- [Prev Class](AQjmsFactory.md)
- [Next Class](AQjmsMessage.md)

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

## Class AQjmsMapMessage

- java.lang.Object

- - [oracle.jms.AQjmsMessage](AQjmsMessage.md)

  - - oracle.jms.AQjmsMapMessage

<!-- -->

- All Implemented Interfaces:
  [MapMessage](../../javax/jms/MapMessage.md), [Message](../../javax/jms/Message.md)

  ------------------------------------------------------------------------



      public class AQjmsMapMessage
      extends AQjmsMessage
      implements MapMessage

  This is an Oracle class which implements `javax.jms.MapMessage`.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Message](../../javax/jms/Message.md)

      [`DEFAULT_DELIVERY_MODE`](../../javax/jms/Message.md)`, `[`DEFAULT_PRIORITY`](../../javax/jms/Message.md)`, `[`DEFAULT_TIME_TO_LIVE`](../../javax/jms/Message.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description                                                                                                                                    |
    |-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                  | `clearBody``()`<br>Clear out the message body.                                                                                                            |
    | `boolean`               | `getBoolean``(java.lang.String name)`<br>Returns the `boolean` value with the specified name.                                                             |
    | `byte`                  | `getByte``(java.lang.String name)`<br>Returns the `byte` value with the specified name.                                                                   |
    | `byte[]`                | `getBytes``(java.lang.String name)`<br>Returns the byte array value with the specified name.                                                              |
    | `char`                  | `getChar``(java.lang.String name)`<br>Returns the Unicode character value with the specified name.                                                        |
    | `double`                | `getDouble``(java.lang.String name)`<br>Returns the `double` value with the specified name.                                                               |
    | `float`                 | `getFloat``(java.lang.String name)`<br>Returns the `float` value with the specified name.                                                                 |
    | `int`                   | `getInt``(java.lang.String name)`<br>Returns the `int` value with the specified name.                                                                     |
    | `long`                  | `getLong``(java.lang.String name)`<br>Returns the `long` value with the specified name.                                                                   |
    | `java.util.Enumeration` | `getMapNames``()`<br>Returns an `Enumeration` of all the names in the `MapMessage` object.                                                                |
    | `java.lang.Object`      | `getObject``(java.lang.String name)`<br>Returns the value of the object with the specified name.                                                          |
    | `short`                 | `getShort``(java.lang.String name)`<br>Returns the `short` value with the specified name.                                                                 |
    | `java.lang.String`      | `getString``(java.lang.String name)`<br>Returns the `String` value with the specified name.                                                               |
    | `boolean`               | `itemExists``(java.lang.String name)`<br>Indicates whether an item exists in this `MapMessage` object.                                                    |
    | `void`                  | `setBoolean``(java.lang.String name, boolean value)`<br>Sets a `boolean` value with the specified name into the Map.                                      |
    | `void`                  | `setByte``(java.lang.String name, byte value)`<br>Sets a `byte` value with the specified name into the Map.                                               |
    | `void`                  | `setBytes``(java.lang.String name, byte[] value)`<br>Sets a byte array value with the specified name into the Map.                                        |
    | `void`                  | `setBytes``(java.lang.String name, byte[] value, int offset, int length)`<br>Sets a portion of the byte array value with the specified name into the Map. |
    | `void`                  | `setChar``(java.lang.String name, char value)`<br>Sets a Unicode character value with the specified name into the Map.                                    |
    | `void`                  | `setDouble``(java.lang.String name, double value)`<br>Sets a `double` value with the specified name into the Map.                                         |
    | `void`                  | `setFloat``(java.lang.String name, float value)`<br>Sets a `float` value with the specified name into the Map.                                            |
    | `void`                  | `setInt``(java.lang.String name, int value)`<br>Sets an `int` value with the specified name into the Map.                                                 |
    | `void`                  | `setLong``(java.lang.String name, long value)`<br>Sets a `long` value with the specified name into the Map.                                               |
    | `void`                  | `setObject``(java.lang.String name, java.lang.Object value)`<br>Sets an object value with the specified name into the Map.                                |
    | `void`                  | `setShort``(java.lang.String name, short value)`<br>Sets a `short` value with the specified name into the Map.                                            |
    | `void`                  | `setString``(java.lang.String name, java.lang.String value)`<br>Sets a `String` value with the specified name into the Map.                               |

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

    - #### setBoolean

          public void setBoolean(java.lang.String name,
                                 boolean value)
                          throws JMSException

      Sets a `boolean` value with the specified name into the Map.
      Specified by:
      [`setBoolean`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `boolean`

      `value` - the `boolean` value to set in the Map

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setByte

          public void setByte(java.lang.String name,
                              byte value)
                       throws JMSException

      Sets a `byte` value with the specified name into the Map.
      Specified by:
      [`setByte`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `byte`

      `value` - the `byte` value to set in the Map

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setShort

          public void setShort(java.lang.String name,
                               short value)
                        throws JMSException

      Sets a `short` value with the specified name into the Map.
      Specified by:
      [`setShort`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `short`

      `value` - the `short` value to set in the Map

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setChar

          public void setChar(java.lang.String name,
                              char value)
                       throws JMSException

      Sets a Unicode character value with the specified name into the Map.
      Specified by:
      [`setChar`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the Unicode character

      `value` - the Unicode character value to set in the Map

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setDouble

          public void setDouble(java.lang.String name,
                                double value)
                         throws JMSException

      Sets a `double` value with the specified name into the Map.
      Specified by:
      [`setDouble`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `double`

      `value` - the `double` value to set in the Map

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setFloat

          public void setFloat(java.lang.String name,
                               float value)
                        throws JMSException

      Sets a `float` value with the specified name into the Map.
      Specified by:
      [`setFloat`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `float`

      `value` - the `float` value to set in the Map

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setInt

          public void setInt(java.lang.String name,
                             int value)
                      throws JMSException

      Sets an `int` value with the specified name into the Map.
      Specified by:
      [`setInt`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `int`

      `value` - the `int` value to set in the Map

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setLong

          public void setLong(java.lang.String name,
                              long value)
                       throws JMSException

      Sets a `long` value with the specified name into the Map.
      Specified by:
      [`setLong`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `long`

      `value` - the `long` value to set in the Map

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setString

          public void setString(java.lang.String name,
                                java.lang.String value)
                         throws JMSException

      Sets a `String` value with the specified name into the Map.
      Specified by:
      [`setString`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `String`

      `value` - the `String` value to set in the Map

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setObject

          public void setObject(java.lang.String name,
                                java.lang.Object value)
                         throws JMSException

      Sets an object value with the specified name into the Map.
      This method works only for the objectified primitive object types (`Integer`, `Double`, `Long` ...), `String` objects, and byte arrays.

      Specified by:
      [`setObject`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the Java object

      `value` - the Java object value to set in the Map

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if the object is invalid.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setBytes

          public void setBytes(java.lang.String name,
                               byte[] value)
                        throws JMSException

      Sets a byte array value with the specified name into the Map.
      Specified by:
      [`setBytes`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the byte array

      `value` - the byte array value to set in the Map; the array is copied so that the value for `name` will not be altered by future modifications

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.NullPointerException` - if the name is null, or if the name is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setBytes

          public void setBytes(java.lang.String name,
                               byte[] value,
                               int offset,
                               int length)
                        throws JMSException

      Sets a portion of the byte array value with the specified name into the Map.
      Specified by:
      [`setBytes`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the byte array

      `value` - the byte array value to set in the Map

      `offset` - the initial offset within the byte array

      `length` - the number of bytes to use

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### getBoolean

          public boolean getBoolean(java.lang.String name)
                             throws JMSException

      Returns the `boolean` value with the specified name.
      Specified by:
      [`getBoolean`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `boolean`

      Returns:
      the `boolean` value with the specified name

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getByte

          public byte getByte(java.lang.String name)
                       throws JMSException

      Returns the `byte` value with the specified name.
      Specified by:
      [`getByte`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `byte`

      Returns:
      the `byte` value with the specified name

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getBytes

          public byte[] getBytes(java.lang.String name)
                          throws JMSException

      Returns the byte array value with the specified name.
      Specified by:
      [`getBytes`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the byte array

      Returns:
      a copy of the byte array value with the specified name; if there is no item by this name, a null value is returned.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getChar

          public char getChar(java.lang.String name)
                       throws JMSException

      Returns the Unicode character value with the specified name.
      Specified by:
      [`getChar`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the Unicode character

      Returns:
      the Unicode character value with the specified name

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getDouble

          public double getDouble(java.lang.String name)
                           throws JMSException

      Returns the `double` value with the specified name.
      Specified by:
      [`getDouble`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `double`

      Returns:
      the `double` value with the specified name

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getFloat

          public float getFloat(java.lang.String name)
                         throws JMSException

      Returns the `float` value with the specified name.
      Specified by:
      [`getFloat`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `float`

      Returns:
      the `float` value with the specified name

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getInt

          public int getInt(java.lang.String name)
                     throws JMSException

      Returns the `int` value with the specified name.
      Specified by:
      [`getInt`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `int`

      Returns:
      the `int` value with the specified name

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getLong

          public long getLong(java.lang.String name)
                       throws JMSException

      Returns the `long` value with the specified name.
      Specified by:
      [`getLong`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `long`

      Returns:
      the `long` value with the specified name

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getMapNames

          public java.util.Enumeration getMapNames()
                                            throws JMSException

      Returns an `Enumeration` of all the names in the `MapMessage` object.
      Specified by:
      [`getMapNames`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Returns:
      an enumeration of all the names in this `MapMessage`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

    <!-- -->

    - #### getObject

          public java.lang.Object getObject(java.lang.String name)
                                     throws JMSException

      Returns the value of the object with the specified name.
      This method can be used to return, in objectified format, an object in the Java programming language ("Java object") that had been stored in the Map with the equivalent `setObject` method call, or its equivalent primitive `set`*`type`* method.

      Note that byte values are returned as `byte[]`, not `Byte[]`.

      Specified by:
      [`getObject`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the Java object

      Returns:
      a copy of the Java object value with the specified name, in objectified format (for example, if the object was set as an `int`, an `Integer` is returned); if there is no item by this name, a null value is returned

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

    <!-- -->

    - #### getShort

          public short getShort(java.lang.String name)
                         throws JMSException

      Returns the `short` value with the specified name.
      Specified by:
      [`getShort`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `short`

      Returns:
      the `short` value with the specified name

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getString

          public java.lang.String getString(java.lang.String name)
                                     throws JMSException

      Returns the `String` value with the specified name.
      Specified by:
      [`getString`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the `String`

      Returns:
      the `String` value with the specified name; if there is no item by this name, a null value is returned

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### itemExists

          public boolean itemExists(java.lang.String name)
                             throws JMSException

      Indicates whether an item exists in this `MapMessage` object.
      Specified by:
      [`itemExists`](../../javax/jms/MapMessage.md) in interface [`MapMessage`](../../javax/jms/MapMessage.md)

      Parameters:
      `name` - the name of the item to test

      Returns:
      true if the item exists

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to determine if the item exists due to some internal error.

    <!-- -->

    - #### clearBody

          public void clearBody()
                         throws JMSException

      Clear out the message body. All other parts of the message are left untouched. The message can now be both read and written to.
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

- [Prev Class](AQjmsFactory.md)
- [Next Class](AQjmsMessage.md)

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
