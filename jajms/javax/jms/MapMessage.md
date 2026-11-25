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

- [Prev Class](JMSSecurityException.md)
- [Next Class](Message.md)

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

## Interface MapMessage

- All Superinterfaces:
  [Message](Message.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsMapMessage](../../oracle/jms/AQjmsMapMessage.md)

  ------------------------------------------------------------------------



      public interface MapMessage
      extends Message

  A `MapMessage` object is used to send a set of name-value pairs. The names are `String` objects, and the values are primitive data types in the Java programming language. The names must have a value that is not null, and not an empty string. The entries can be accessed sequentially or randomly by name. The order of the entries is undefined. `MapMessage` inherits from the `Message` interface and adds a message body that contains a Map.
  The primitive types can be read or written explicitly using methods for each type. They may also be read or written generically as objects. For instance, a call to `MapMessage.setInt("foo", 6)` is equivalent to `MapMessage.setObject("foo", new Integer(6))`. Both forms are provided, because the explicit form is convenient for static programming, and the object form is needed when types are not known at compile time.

  When a client receives a `MapMessage`, it is in read-only mode. If a client attempts to write to the message at this point, a `MessageNotWriteableException` is thrown. If `clearBody` is called, the message can now be both read from and written to.

  `MapMessage` objects support the following conversion table. The marked cases must be supported. The unmarked cases must throw a `JMSException`. The `String`-to-primitive conversions may throw a runtime exception if the primitive's `valueOf()` method does not accept it as a valid `String` representation of the primitive.

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
  [`Session.createMapMessage()`](Session.md), [`BytesMessage`](BytesMessage.md), [`Message`](Message.md), [`ObjectMessage`](ObjectMessage.md), [`StreamMessage`](StreamMessage.md), [`TextMessage`](TextMessage.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Message](Message.md)

      [`DEFAULT_DELIVERY_MODE`](Message.md)`, `[`DEFAULT_PRIORITY`](Message.md)`, `[`DEFAULT_TIME_TO_LIVE`](Message.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type       | Method and Description                                                                                                                                    |
    |-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
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

    - ### Methods inherited from interface javax.jms.[Message](Message.md)

      [`acknowledge`](Message.md)`, `[`clearBody`](Message.md)`, `[`clearProperties`](Message.md)`, `[`getBooleanProperty`](Message.md)`, `[`getByteProperty`](Message.md)`, `[`getDoubleProperty`](Message.md)`, `[`getFloatProperty`](Message.md)`, `[`getIntProperty`](Message.md)`, `[`getJMSCorrelationID`](Message.md)`, `[`getJMSCorrelationIDAsBytes`](Message.md)`, `[`getJMSDeliveryMode`](Message.md)`, `[`getJMSDestination`](Message.md)`, `[`getJMSExpiration`](Message.md)`, `[`getJMSMessageID`](Message.md)`, `[`getJMSPriority`](Message.md)`, `[`getJMSRedelivered`](Message.md)`, `[`getJMSReplyTo`](Message.md)`, `[`getJMSTimestamp`](Message.md)`, `[`getJMSType`](Message.md)`, `[`getLongProperty`](Message.md)`, `[`getObjectProperty`](Message.md)`, `[`getPropertyNames`](Message.md)`, `[`getShortProperty`](Message.md)`, `[`getStringProperty`](Message.md)`, `[`propertyExists`](Message.md)`, `[`setBooleanProperty`](Message.md)`, `[`setByteProperty`](Message.md)`, `[`setDoubleProperty`](Message.md)`, `[`setFloatProperty`](Message.md)`, `[`setIntProperty`](Message.md)`, `[`setJMSCorrelationID`](Message.md)`, `[`setJMSCorrelationIDAsBytes`](Message.md)`, `[`setJMSDeliveryMode`](Message.md)`, `[`setJMSDestination`](Message.md)`, `[`setJMSExpiration`](Message.md)`, `[`setJMSMessageID`](Message.md)`, `[`setJMSPriority`](Message.md)`, `[`setJMSRedelivered`](Message.md)`, `[`setJMSReplyTo`](Message.md)`, `[`setJMSTimestamp`](Message.md)`, `[`setJMSType`](Message.md)`, `[`setLongProperty`](Message.md)`, `[`setObjectProperty`](Message.md)`, `[`setShortProperty`](Message.md)`, `[`setStringProperty`](Message.md)

<!-- -->

- - ### Method Detail

    - #### getBoolean

          boolean getBoolean(java.lang.String name)
                      throws JMSException

      Returns the `boolean` value with the specified name.
      Parameters:
      `name` - the name of the `boolean`

      Returns:
      the `boolean` value with the specified name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getByte

          byte getByte(java.lang.String name)
                throws JMSException

      Returns the `byte` value with the specified name.
      Parameters:
      `name` - the name of the `byte`

      Returns:
      the `byte` value with the specified name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getShort

          short getShort(java.lang.String name)
                  throws JMSException

      Returns the `short` value with the specified name.
      Parameters:
      `name` - the name of the `short`

      Returns:
      the `short` value with the specified name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getChar

          char getChar(java.lang.String name)
                throws JMSException

      Returns the Unicode character value with the specified name.
      Parameters:
      `name` - the name of the Unicode character

      Returns:
      the Unicode character value with the specified name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getInt

          int getInt(java.lang.String name)
              throws JMSException

      Returns the `int` value with the specified name.
      Parameters:
      `name` - the name of the `int`

      Returns:
      the `int` value with the specified name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getLong

          long getLong(java.lang.String name)
                throws JMSException

      Returns the `long` value with the specified name.
      Parameters:
      `name` - the name of the `long`

      Returns:
      the `long` value with the specified name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getFloat

          float getFloat(java.lang.String name)
                  throws JMSException

      Returns the `float` value with the specified name.
      Parameters:
      `name` - the name of the `float`

      Returns:
      the `float` value with the specified name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getDouble

          double getDouble(java.lang.String name)
                    throws JMSException

      Returns the `double` value with the specified name.
      Parameters:
      `name` - the name of the `double`

      Returns:
      the `double` value with the specified name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getString

          java.lang.String getString(java.lang.String name)
                              throws JMSException

      Returns the `String` value with the specified name.
      Parameters:
      `name` - the name of the `String`

      Returns:
      the `String` value with the specified name; if there is no item by this name, a null value is returned

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getBytes

          byte[] getBytes(java.lang.String name)
                   throws JMSException

      Returns the byte array value with the specified name.
      Parameters:
      `name` - the name of the byte array

      Returns:
      a copy of the byte array value with the specified name; if there is no item by this name, a null value is returned.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getObject

          java.lang.Object getObject(java.lang.String name)
                              throws JMSException

      Returns the value of the object with the specified name.
      This method can be used to return, in objectified format, an object in the Java programming language ("Java object") that had been stored in the Map with the equivalent `setObject` method call, or its equivalent primitive `set`*`type`* method.

      Note that byte values are returned as `byte[]`, not `Byte[]`.

      Parameters:
      `name` - the name of the Java object

      Returns:
      a copy of the Java object value with the specified name, in objectified format (for example, if the object was set as an `int`, an `Integer` is returned); if there is no item by this name, a null value is returned

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

    <!-- -->

    - #### getMapNames

          java.util.Enumeration getMapNames()
                                     throws JMSException

      Returns an `Enumeration` of all the names in the `MapMessage` object.
      Returns:
      an enumeration of all the names in this `MapMessage`

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to read the message due to some internal error.

    <!-- -->

    - #### setBoolean

          void setBoolean(java.lang.String name,
                          boolean value)
                   throws JMSException

      Sets a `boolean` value with the specified name into the Map.
      Parameters:
      `name` - the name of the `boolean`

      `value` - the `boolean` value to set in the Map

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setByte

          void setByte(java.lang.String name,
                       byte value)
                throws JMSException

      Sets a `byte` value with the specified name into the Map.
      Parameters:
      `name` - the name of the `byte`

      `value` - the `byte` value to set in the Map

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setShort

          void setShort(java.lang.String name,
                        short value)
                 throws JMSException

      Sets a `short` value with the specified name into the Map.
      Parameters:
      `name` - the name of the `short`

      `value` - the `short` value to set in the Map

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setChar

          void setChar(java.lang.String name,
                       char value)
                throws JMSException

      Sets a Unicode character value with the specified name into the Map.
      Parameters:
      `name` - the name of the Unicode character

      `value` - the Unicode character value to set in the Map

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setInt

          void setInt(java.lang.String name,
                      int value)
               throws JMSException

      Sets an `int` value with the specified name into the Map.
      Parameters:
      `name` - the name of the `int`

      `value` - the `int` value to set in the Map

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setLong

          void setLong(java.lang.String name,
                       long value)
                throws JMSException

      Sets a `long` value with the specified name into the Map.
      Parameters:
      `name` - the name of the `long`

      `value` - the `long` value to set in the Map

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setFloat

          void setFloat(java.lang.String name,
                        float value)
                 throws JMSException

      Sets a `float` value with the specified name into the Map.
      Parameters:
      `name` - the name of the `float`

      `value` - the `float` value to set in the Map

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setDouble

          void setDouble(java.lang.String name,
                         double value)
                  throws JMSException

      Sets a `double` value with the specified name into the Map.
      Parameters:
      `name` - the name of the `double`

      `value` - the `double` value to set in the Map

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setString

          void setString(java.lang.String name,
                         java.lang.String value)
                  throws JMSException

      Sets a `String` value with the specified name into the Map.
      Parameters:
      `name` - the name of the `String`

      `value` - the `String` value to set in the Map

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setBytes

          void setBytes(java.lang.String name,
                        byte[] value)
                 throws JMSException

      Sets a byte array value with the specified name into the Map.
      Parameters:
      `name` - the name of the byte array

      `value` - the byte array value to set in the Map; the array is copied so that the value for `name` will not be altered by future modifications

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.NullPointerException` - if the name is null, or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setBytes

          void setBytes(java.lang.String name,
                        byte[] value,
                        int offset,
                        int length)
                 throws JMSException

      Sets a portion of the byte array value with the specified name into the Map.
      Parameters:
      `name` - the name of the byte array

      `value` - the byte array value to set in the Map

      `offset` - the initial offset within the byte array

      `length` - the number of bytes to use

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### setObject

          void setObject(java.lang.String name,
                         java.lang.Object value)
                  throws JMSException

      Sets an object value with the specified name into the Map.
      This method works only for the objectified primitive object types (`Integer`, `Double`, `Long` ...), `String` objects, and byte arrays.

      Parameters:
      `name` - the name of the Java object

      `value` - the Java object value to set in the Map

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to write the message due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageFormatException`](MessageFormatException.md) - if the object is invalid.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if the message is in read-only mode.

    <!-- -->

    - #### itemExists

          boolean itemExists(java.lang.String name)
                      throws JMSException

      Indicates whether an item exists in this `MapMessage` object.
      Parameters:
      `name` - the name of the item to test

      Returns:
      true if the item exists

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to determine if the item exists due to some internal error.

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

- [Prev Class](JMSSecurityException.md)
- [Next Class](Message.md)

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
