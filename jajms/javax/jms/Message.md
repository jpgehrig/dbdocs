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

- [Prev Class](MapMessage.md)
- [Next Class](MessageConsumer.md)

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

## Interface Message

- All Known Subinterfaces:
  [AdtMessage](../../oracle/jms/AdtMessage.md), [BytesMessage](BytesMessage.md), [MapMessage](MapMessage.md), [ObjectMessage](ObjectMessage.md), [StreamMessage](StreamMessage.md), [TextMessage](TextMessage.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsAdtMessage](../../oracle/jms/AQjmsAdtMessage.md), [AQjmsBytesMessage](../../oracle/jms/AQjmsBytesMessage.md), [AQjmsMapMessage](../../oracle/jms/AQjmsMapMessage.md), [AQjmsMessage](../../oracle/jms/AQjmsMessage.md), [AQjmsObjectMessage](../../oracle/jms/AQjmsObjectMessage.md), [AQjmsStreamMessage](../../oracle/jms/AQjmsStreamMessage.md), [AQjmsTextMessage](../../oracle/jms/AQjmsTextMessage.md)

  ------------------------------------------------------------------------



      public interface Message

  The `Message` interface is the root interface of all JMS messages. It defines the message header and the `acknowledge` method used for all messages.
  Most message-oriented middleware (MOM) products treat messages as lightweight entities that consist of a header and a payload. The header contains fields used for message routing and identification; the payload contains the application data being sent.

  Within this general form, the definition of a message varies significantly across products. It would be quite difficult for the JMS API to support all of these message models.

  With this in mind, the JMS message model has the following goals:

  - Provide a single, unified message API
  - Provide an API suitable for creating messages that match the format used by provider-native messaging applications
  - Support the development of heterogeneous applications that span operating systems, machine architectures, and computer languages
  - Support messages containing objects in the Java programming language ("Java objects")
  - Support messages containing Extensible Markup Language (XML) pages

  JMS messages are composed of the following parts:

  - Header - All messages support the same set of header fields. Header fields contain values used by both clients and providers to identify and route messages.
  - Properties - Each message contains a built-in facility for supporting application-defined property values. Properties provide an efficient mechanism for supporting application-defined message filtering.
  - Body - The JMS API defines several types of message body, which cover the majority of messaging styles currently in use.

  #### Message Bodies

  The JMS API defines five types of message body:

  - Stream - A `StreamMessage` object's message body contains a stream of primitive values in the Java programming language ("Java primitives"). It is filled and read sequentially.
  - Map - A `MapMessage` object's message body contains a set of name-value pairs, where names are `String` objects, and values are Java primitives. The entries can be accessed sequentially or randomly by name. The order of the entries is undefined.
  - Text - A `TextMessage` object's message body contains a `java.lang.String` object. This message type can be used to transport plain-text messages, and XML messages.
  - Object - An `ObjectMessage` object's message body contains a `Serializable` Java object.
  - Bytes - A `BytesMessage` object's message body contains a stream of uninterpreted bytes. This message type is for literally encoding a body to match an existing message format. In many cases, it is possible to use one of the other body types, which are easier to use. Although the JMS API allows the use of message properties with byte messages, they are typically not used, since the inclusion of properties may affect the format.

  #### Message Headers

  The `JMSCorrelationID` header field is used for linking one message with another. It typically links a reply message with its requesting message.

  `JMSCorrelationID` can hold a provider-specific message ID, an application-specific `String` object, or a provider-native `byte[]` value.

  #### Message Properties

  A `Message` object contains a built-in facility for supporting application-defined property values. In effect, this provides a mechanism for adding application-specific header fields to a message.

  Properties allow an application, via message selectors, to have a JMS provider select, or filter, messages on its behalf using application-specific criteria.

  Property names must obey the rules for a message selector identifier. Property names must not be null, and must not be empty strings. If a property name is set and it is either null or an empty string, an `IllegalArgumentException` must be thrown.

  Property values can be `boolean`, `byte`, `short`, `int`, `long`, `float`, `double`, and `String`.

  Property values are set prior to sending a message. When a client receives a message, its properties are in read-only mode. If a client attempts to set properties at this point, a `MessageNotWriteableException` is thrown. If `clearProperties` is called, the properties can now be both read from and written to. Note that header fields are distinct from properties. Header fields are never in read-only mode.

  A property value may duplicate a value in a message's body, or it may not. Although JMS does not define a policy for what should or should not be made a property, application developers should note that JMS providers will likely handle data in a message's body more efficiently than data in a message's properties. For best performance, applications should use message properties only when they need to customize a message's header. The primary reason for doing this is to support customized message selection.

  Message properties support the following conversion table. The marked cases must be supported. The unmarked cases must throw a `JMSException`. The `String`-to-primitive conversions may throw a runtime exception if the primitive's `valueOf` method does not accept the `String` as a valid representation of the primitive.

  A value written as the row type can be read as the column type.

       |        | boolean byte short int long float double String
       |----------------------------------------------------------
       |boolean |    X                                       X
       |byte    |          X     X    X   X                  X
       |short   |                X    X   X                  X
       |int     |                     X   X                  X
       |long    |                         X                  X
       |float   |                               X     X      X
       |double  |                                     X      X
       |String  |    X     X     X    X   X     X     X      X
       |----------------------------------------------------------


  In addition to the type-specific set/get methods for properties, JMS provides the `setObjectProperty` and `getObjectProperty` methods. These support the same set of property types using the objectified primitive values. Their purpose is to allow the decision of property type to made at execution time rather than at compile time. They support the same property value conversions.

  The `setObjectProperty` method accepts values of class `Boolean`, `Byte`, `Short`, `Integer`, `Long`, `Float`, `Double`, and `String`. An attempt to use any other class must throw a `JMSException`.

  The `getObjectProperty` method only returns values of class `Boolean`, `Byte`, `Short`, `Integer`, `Long`, `Float`, `Double`, and `String`.

  The order of property values is not defined. To iterate through a message's property values, use `getPropertyNames` to retrieve a property name enumeration and then use the various property get methods to retrieve their values.

  A message's properties are deleted by the `clearProperties` method. This leaves the message with an empty set of properties.

  Getting a property value for a name which has not been set returns a null value. Only the `getStringProperty` and `getObjectProperty` methods can return a null value. Attempting to read a null value as a primitive type must be treated as calling the primitive's corresponding `valueOf(String)` conversion method with a null value.

  The JMS API reserves the `JMSX` property name prefix for JMS defined properties. The full set of these properties is defined in the Java Message Service specification. New JMS defined properties may be added in later versions of the JMS API. Support for these properties is optional. The `String[] ConnectionMetaData.getJMSXPropertyNames` method returns the names of the JMSX properties supported by a connection.

  JMSX properties may be referenced in message selectors whether or not they are supported by a connection. If they are not present in a message, they are treated like any other absent property.

  JMSX properties defined in the specification as "set by provider on send" are available to both the producer and the consumers of the message. JMSX properties defined in the specification as "set by provider on receive" are available only to the consumers.

  `JMSXGroupID` and `JMSXGroupSeq` are standard properties that clients should use if they want to group messages. All providers must support them. Unless specifically noted, the values and semantics of the JMSX properties are undefined.

  The JMS API reserves the `JMS_`*`vendor_name`* property name prefix for provider-specific properties. Each provider defines its own value for *`vendor_name`*. This is the mechanism a JMS provider uses to make its special per-message services available to a JMS client.

  The purpose of provider-specific properties is to provide special features needed to integrate JMS clients with provider-native clients in a single JMS application. They should not be used for messaging between JMS clients.

  #### Provider Implementations of JMS Message Interfaces

  The JMS API provides a set of message interfaces that define the JMS message model. It does not provide implementations of these interfaces.

  Each JMS provider supplies a set of message factories with its `Session` object for creating instances of messages. This allows a provider to use message implementations tailored to its specific needs.

  A provider must be prepared to accept message implementations that are not its own. They may not be handled as efficiently as its own implementation; however, they must be handled.

  Note the following exception case when a provider is handling a foreign message implementation. If the foreign message implementation contains a `JMSReplyTo` header field that is set to a foreign destination implementation, the provider is not required to handle or preserve the value of this header field.

  #### Message Selectors

  A JMS message selector allows a client to specify, by header field references and property references, the messages it is interested in. Only messages whose header and property values match the selector are delivered. What it means for a message not to be delivered depends on the `MessageConsumer` being used (see [`QueueReceiver`](QueueReceiver.md) and [`TopicSubscriber`](TopicSubscriber.md)).

  Message selectors cannot reference message body values.

  A message selector matches a message if the selector evaluates to true when the message's header field values and property values are substituted for their corresponding identifiers in the selector.

  A message selector is a `String` whose syntax is based on a subset of the SQL92 conditional expression syntax. If the value of a message selector is an empty string, the value is treated as a null and indicates that there is no message selector for the message consumer.

  The order of evaluation of a message selector is from left to right within precedence level. Parentheses can be used to change this order.

  Predefined selector literals and operator names are shown here in uppercase; however, they are case insensitive.

  A selector can contain:

  - Literals:
    - A string literal is enclosed in single quotes, with a single quote represented by doubled single quote; for example, `'literal'` and `'literal''s'`. Like string literals in the Java programming language, these use the Unicode character encoding.
    - An exact numeric literal is a numeric value without a decimal point, such as `57`, `-957`, and `+62`; numbers in the range of `long` are supported. Exact numeric literals use the integer literal syntax of the Java programming language.
    - An approximate numeric literal is a numeric value in scientific notation, such as `7E3` and `-57.9E2`, or a numeric value with a decimal, such as `7.`, `-95.7`, and `+6.2`; numbers in the range of `double` are supported. Approximate literals use the floating-point literal syntax of the Java programming language.
    - The boolean literals `TRUE` and `FALSE`.

  - Identifiers:
    - An identifier is an unlimited-length sequence of letters and digits, the first of which must be a letter. A letter is any character for which the method `Character.isJavaLetter` returns true. This includes `'_'` and `'$'`. A letter or digit is any character for which the method `Character.isJavaLetterOrDigit` returns true.

    - Identifiers cannot be the names `NULL`, `TRUE`, and `FALSE`.

    - Identifiers cannot be `NOT`, `AND`, `OR`, `BETWEEN`, `LIKE`, `IN`, `IS`, or `ESCAPE`.

    - Identifiers are either header field references or property references. The type of a property value in a message selector corresponds to the type used to set the property. If a property that does not exist in a message is referenced, its value is `NULL`.

    - The conversions that apply to the get methods for properties do not apply when a property is used in a message selector expression. For example, suppose you set a property as a string value, as in the following:

          myMessage.setStringProperty("NumberOfOrders", "2");

      The following expression in a message selector would evaluate to false, because a string cannot be used in an arithmetic expression:

          "NumberOfOrders > 1"

    - Identifiers are case-sensitive.

    - Message header field references are restricted to `JMSDeliveryMode`, `JMSPriority`, `JMSMessageID`, `JMSTimestamp`, `JMSCorrelationID`, and `JMSType`. `JMSMessageID`, `JMSCorrelationID`, and `JMSType` values may be null and if so are treated as a `NULL` value.

    - Any name beginning with `'JMSX'` is a JMS defined property name.

    - Any name beginning with `'JMS_'` is a provider-specific property name.

    - Any name that does not begin with `'JMS'` is an application-specific property name.

  - White space is the same as that defined for the Java programming language: space, horizontal tab, form feed, and line terminator.

  - Expressions:
    - A selector is a conditional expression; a selector that evaluates to `true` matches; a selector that evaluates to `false` or unknown does not match.
    - Arithmetic expressions are composed of themselves, arithmetic operations, identifiers (whose value is treated as a numeric literal), and numeric literals.
    - Conditional expressions are composed of themselves, comparison operations, and logical operations.

  - Standard bracketing `()` for ordering expression evaluation is supported.

  - Logical operators in precedence order: `NOT`, `AND`, `OR`

  - Comparison operators: `=`, `>`, `>=`, `<`, `<=`, `<>` (not equal)
    - Only like type values can be compared. One exception is that it is valid to compare exact numeric values and approximate numeric values; the type conversion required is defined by the rules of numeric promotion in the Java programming language. If the comparison of non-like type values is attempted, the value of the operation is false. If either of the type values evaluates to `NULL`, the value of the expression is unknown.
    - String and boolean comparison is restricted to `=` and `<>`. Two strings are equal if and only if they contain the same sequence of characters.

  - Arithmetic operators in precedence order:
    - `+`, `-` (unary)
    - `*`, `/` (multiplication and division)
    - `+`, `-` (addition and subtraction)
    - Arithmetic operations must use numeric promotion in the Java programming language.

  - *`arithmetic-expr1`*` [NOT] BETWEEN `*`arithmetic-expr2`*` AND `*`arithmetic-expr3`* (comparison operator)
    - `"age BETWEEN 15 AND 19"` is equivalent to `"age >= 15 AND age <= 19"`
    - `"age NOT BETWEEN 15 AND 19"` is equivalent to `"age < 15 OR age > 19"`

  - *`identifier`*` [NOT] IN (`*`string-literal1`*`, `*`string-literal2`*`,...)` (comparison operator where *`identifier`* has a `String` or `NULL` value)
    - `"Country IN (' UK', 'US', 'France')"` is true for `'UK'` and false for `'Peru'`; it is equivalent to the expression `"(Country = ' UK') OR (Country = ' US') OR (Country = ' France')"`
    - `"Country NOT IN (' UK', 'US', 'France')"` is false for `'UK'` and true for `'Peru'`; it is equivalent to the expression `"NOT ((Country = ' UK') OR (Country = ' US') OR (Country = ' France'))"`
    - If identifier of an `IN` or `NOT IN` operation is `NULL`, the value of the operation is unknown.

  - *`identifier`*` [NOT] LIKE `*`pattern-value`*` [ESCAPE `*`escape-character`*`]` (comparison operator, where *`identifier`* has a `String` value; *`pattern-value`* is a string literal where `'_'` stands for any single character; `'%'` stands for any sequence of characters, including the empty sequence; and all other characters stand for themselves. The optional *`escape-character`* is a single-character string literal whose character is used to escape the special meaning of the `'_'` and `'%'` in *`pattern-value`*.)
    - `"phone LIKE '12%3'"` is true for `'123'` or `'12993'` and false for `'1234'`
    - `"word LIKE 'l_se'"` is true for `'lose'` and false for `'loose'`
    - `"underscored LIKE '\_%' ESCAPE '\'"` is true for `'_foo'` and false for `'bar'`
    - `"phone NOT LIKE '12%3'"` is false for `'123'` or `'12993'` and true for `'1234'`
    - If *`identifier`* of a `LIKE` or `NOT LIKE` operation is `NULL`, the value of the operation is unknown.

  - *`identifier`*` IS NULL` (comparison operator that tests for a null header field value or a missing property value)
    - `"prop_name IS NULL"`

  - *`identifier`*` IS NOT NULL` (comparison operator that tests for the existence of a non-null header field value or a property value)

    - `"prop_name IS NOT NULL"`

    JMS providers are required to verify the syntactic correctness of a message selector at the time it is presented. A method that provides a syntactically incorrect selector must result in a `JMSException`. JMS providers may also optionally provide some semantic checking at the time the selector is presented. Not all semantic checking can be performed at the time a message selector is presented, because property types are not known.

    The following message selector selects messages with a message type of car and color of blue and weight greater than 2500 pounds:

        "JMSType = 'car' AND color = 'blue' AND weight > 2500"

    #### Null Values

    As noted above, property values may be `NULL`. The evaluation of selector expressions containing `NULL` values is defined by SQL92 `NULL` semantics. A brief description of these semantics is provided here.

    SQL treats a `NULL` value as unknown. Comparison or arithmetic with an unknown value always yields an unknown value.

    The `IS NULL` and `IS NOT NULL` operators convert an unknown value into the respective `TRUE` and `FALSE` values.

    The boolean operators use three-valued logic as defined by the following tables:

    **The definition of the `AND` operator**

         | AND  |   T   |   F   |   U
         +------+-------+-------+-------
         |  T   |   T   |   F   |   U
         |  F   |   F   |   F   |   F
         |  U   |   U   |   F   |   U
         +------+-------+-------+-------


    **The definition of the `OR` operator**

         | OR   |   T   |   F   |   U
         +------+-------+-------+--------
         |  T   |   T   |   T   |   T
         |  F   |   T   |   F   |   U
         |  U   |   T   |   U   |   U
         +------+-------+-------+-------


    **The definition of the `NOT` operator**

         | NOT
         +------+------
         |  T   |   F
         |  F   |   T
         |  U   |   U
         +------+-------


    #### Special Notes

    When used in a message selector, the `JMSDeliveryMode` header field is treated as having the values `'PERSISTENT'` and `'NON_PERSISTENT'`.

    Date and time values should use the standard `long` millisecond value. When a date or time literal is included in a message selector, it should be an integer literal for a millisecond value. The standard way to produce millisecond values is to use `java.util.Calendar`.

    Although SQL supports fixed decimal comparison and arithmetic, JMS message selectors do not. This is the reason for restricting exact numeric literals to those without a decimal (and the addition of numerics with a decimal as an alternate representation for approximate numeric values).

    SQL comments are not supported.

  See Also:
  [`MessageConsumer.receive()`](MessageConsumer.md), [`MessageConsumer.receive(long)`](MessageConsumer.md), [`MessageConsumer.receiveNoWait()`](MessageConsumer.md), [`MessageListener.onMessage(Message)`](MessageListener.md), [`BytesMessage`](BytesMessage.md), [`MapMessage`](MapMessage.md), [`ObjectMessage`](ObjectMessage.md), [`StreamMessage`](StreamMessage.md), [`TextMessage`](TextMessage.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                          |
    |-------------------|----------------------------------------------------------------------------------------------------------------|
    | `static int`      | `DEFAULT_DELIVERY_MODE`<br>The message producer's default delivery mode is `PERSISTENT`.                       |
    | `static int`      | `DEFAULT_PRIORITY`<br>The message producer's default priority is 4.                                            |
    | `static long`     | `DEFAULT_TIME_TO_LIVE`<br>The message producer's default time to live is unlimited; the message never expires. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type               | Method and Description                                                                                                                              |
    |---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                          | `acknowledge``()`<br>Acknowledges all consumed messages of the session of this consumed message.                                                    |
    | `void`                          | `clearBody``()`<br>Clears out the message body.                                                                                                     |
    | `void`                          | `clearProperties``()`<br>Clears a message's properties.                                                                                             |
    | `boolean`                       | `getBooleanProperty``(java.lang.String name)`<br>Returns the value of the `boolean` property with the specified name.                               |
    | `byte`                          | `getByteProperty``(java.lang.String name)`<br>Returns the value of the `byte` property with the specified name.                                     |
    | `double`                        | `getDoubleProperty``(java.lang.String name)`<br>Returns the value of the `double` property with the specified name.                                 |
    | `float`                         | `getFloatProperty``(java.lang.String name)`<br>Returns the value of the `float` property with the specified name.                                   |
    | `int`                           | `getIntProperty``(java.lang.String name)`<br>Returns the value of the `int` property with the specified name.                                       |
    | `java.lang.String`              | `getJMSCorrelationID``()`<br>Gets the correlation ID for the message.                                                                               |
    | `byte[]`                        | `getJMSCorrelationIDAsBytes``()`<br>Gets the correlation ID as an array of bytes for the message.                                                   |
    | `int`                           | `getJMSDeliveryMode``()`<br>Gets the `DeliveryMode` value specified for this message.                                                               |
    | [`Destination`](Destination.md) | `getJMSDestination``()`<br>Gets the `Destination` object for this message.                                                                          |
    | `long`                          | `getJMSExpiration``()`<br>Gets the message's expiration value.                                                                                      |
    | `java.lang.String`              | `getJMSMessageID``()`<br>Gets the message ID.                                                                                                       |
    | `int`                           | `getJMSPriority``()`<br>Gets the message priority level.                                                                                            |
    | `boolean`                       | `getJMSRedelivered``()`<br>Gets an indication of whether this message is being redelivered.                                                         |
    | [`Destination`](Destination.md) | `getJMSReplyTo``()`<br>Gets the `Destination` object to which a reply to this message should be sent.                                               |
    | `long`                          | `getJMSTimestamp``()`<br>Gets the message timestamp.                                                                                                |
    | `java.lang.String`              | `getJMSType``()`<br>Gets the message type identifier supplied by the client when the message was sent.                                              |
    | `long`                          | `getLongProperty``(java.lang.String name)`<br>Returns the value of the `long` property with the specified name.                                     |
    | `java.lang.Object`              | `getObjectProperty``(java.lang.String name)`<br>Returns the value of the Java object property with the specified name.                              |
    | `java.util.Enumeration`         | `getPropertyNames``()`<br>Returns an `Enumeration` of all the property names.                                                                       |
    | `short`                         | `getShortProperty``(java.lang.String name)`<br>Returns the value of the `short` property with the specified name.                                   |
    | `java.lang.String`              | `getStringProperty``(java.lang.String name)`<br>Returns the value of the `String` property with the specified name.                                 |
    | `boolean`                       | `propertyExists``(java.lang.String name)`<br>Indicates whether a property value exists.                                                             |
    | `void`                          | `setBooleanProperty``(java.lang.String name, boolean value)`<br>Sets a `boolean` property value with the specified name into the message.           |
    | `void`                          | `setByteProperty``(java.lang.String name, byte value)`<br>Sets a `byte` property value with the specified name into the message.                    |
    | `void`                          | `setDoubleProperty``(java.lang.String name, double value)`<br>Sets a `double` property value with the specified name into the message.              |
    | `void`                          | `setFloatProperty``(java.lang.String name, float value)`<br>Sets a `float` property value with the specified name into the message.                 |
    | `void`                          | `setIntProperty``(java.lang.String name, int value)`<br>Sets an `int` property value with the specified name into the message.                      |
    | `void`                          | `setJMSCorrelationID``(java.lang.String correlationID)`<br>Sets the correlation ID for the message.                                                 |
    | `void`                          | `setJMSCorrelationIDAsBytes``(byte[] correlationID)`<br>Sets the correlation ID as an array of bytes for the message.                               |
    | `void`                          | `setJMSDeliveryMode``(int deliveryMode)`<br>Sets the `DeliveryMode` value for this message.                                                         |
    | `void`                          | `setJMSDestination``(`[`Destination`](Destination.md)` destination)`<br>Sets the `Destination` object for this message.                             |
    | `void`                          | `setJMSExpiration``(long expiration)`<br>Sets the message's expiration value.                                                                       |
    | `void`                          | `setJMSMessageID``(java.lang.String id)`<br>Sets the message ID.                                                                                    |
    | `void`                          | `setJMSPriority``(int priority)`<br>Sets the priority level for this message.                                                                       |
    | `void`                          | `setJMSRedelivered``(boolean redelivered)`<br>Specifies whether this message is being redelivered.                                                  |
    | `void`                          | `setJMSReplyTo``(`[`Destination`](Destination.md)` replyTo)`<br>Sets the `Destination` object to which a reply to this message should be sent.      |
    | `void`                          | `setJMSTimestamp``(long timestamp)`<br>Sets the message timestamp.                                                                                  |
    | `void`                          | `setJMSType``(java.lang.String type)`<br>Sets the message type.                                                                                     |
    | `void`                          | `setLongProperty``(java.lang.String name, long value)`<br>Sets a `long` property value with the specified name into the message.                    |
    | `void`                          | `setObjectProperty``(java.lang.String name, java.lang.Object value)`<br>Sets a Java object property value with the specified name into the message. |
    | `void`                          | `setShortProperty``(java.lang.String name, short value)`<br>Sets a `short` property value with the specified name into the message.                 |
    | `void`                          | `setStringProperty``(java.lang.String name, java.lang.String value)`<br>Sets a `String` property value with the specified name into the message.    |

<!-- -->

- - ### Field Detail

    - #### DEFAULT_DELIVERY_MODE

          static final int DEFAULT_DELIVERY_MODE

      The message producer's default delivery mode is `PERSISTENT`.
      See Also:
      [`DeliveryMode.PERSISTENT`](DeliveryMode.md), [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DEFAULT_PRIORITY

          static final int DEFAULT_PRIORITY

      The message producer's default priority is 4.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DEFAULT_TIME_TO_LIVE

          static final long DEFAULT_TIME_TO_LIVE

      The message producer's default time to live is unlimited; the message never expires.
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getJMSMessageID

          java.lang.String getJMSMessageID()
                                    throws JMSException

      Gets the message ID.
      The `JMSMessageID` header field contains a value that uniquely identifies each message sent by a provider.

      When a message is sent, `JMSMessageID` can be ignored. When the `send` or `publish` method returns, it contains a provider-assigned value.

      A `JMSMessageID` is a `String` value that should function as a unique key for identifying messages in a historical repository. The exact scope of uniqueness is provider-defined. It should at least cover all messages for a specific installation of a provider, where an installation is some connected set of message routers.

      All `JMSMessageID` values must start with the prefix `'ID:'`. Uniqueness of message ID values across different providers is not required.

      Since message IDs take some effort to create and increase a message's size, some JMS providers may be able to optimize message overhead if they are given a hint that the message ID is not used by an application. By calling the `MessageProducer.setDisableMessageID` method, a JMS client enables this potential optimization for all messages sent by that message producer. If the JMS provider accepts this hint, these messages must have the message ID set to null; if the provider ignores the hint, the message ID must be set to its normal unique value.

      Returns:
      the message ID

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the message ID due to some internal error.

      See Also:
      `Message.setJMSMessageID(String)`, [`MessageProducer.setDisableMessageID(boolean)`](MessageProducer.md)

    <!-- -->

    - #### setJMSMessageID

          void setJMSMessageID(java.lang.String id)
                        throws JMSException

      Sets the message ID.
      JMS providers set this field when a message is sent. This method can be used to change the value for a message that has been received.

      Parameters:
      `id` - the ID of the message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the message ID due to some internal error.

      See Also:
      `Message.getJMSMessageID()`

    <!-- -->

    - #### getJMSTimestamp

          long getJMSTimestamp()
                        throws JMSException

      Gets the message timestamp.
      The `JMSTimestamp` header field contains the time a message was handed off to a provider to be sent. It is not the time the message was actually transmitted, because the actual send may occur later due to transactions or other client-side queueing of messages.

      When a message is sent, `JMSTimestamp` is ignored. When the `send` or `publish` method returns, it contains a time value somewhere in the interval between the call and the return. The value is in the format of a normal millis time value in the Java programming language.

      Since timestamps take some effort to create and increase a message's size, some JMS providers may be able to optimize message overhead if they are given a hint that the timestamp is not used by an application. By calling the `MessageProducer.setDisableMessageTimestamp` method, a JMS client enables this potential optimization for all messages sent by that message producer. If the JMS provider accepts this hint, these messages must have the timestamp set to zero; if the provider ignores the hint, the timestamp must be set to its normal value.

      Returns:
      the message timestamp

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the timestamp due to some internal error.

      See Also:
      `Message.setJMSTimestamp(long)`, [`MessageProducer.setDisableMessageTimestamp(boolean)`](MessageProducer.md)

    <!-- -->

    - #### setJMSTimestamp

          void setJMSTimestamp(long timestamp)
                        throws JMSException

      Sets the message timestamp.
      JMS providers set this field when a message is sent. This method can be used to change the value for a message that has been received.

      Parameters:
      `timestamp` - the timestamp for this message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the timestamp due to some internal error.

      See Also:
      `Message.getJMSTimestamp()`

    <!-- -->

    - #### getJMSCorrelationIDAsBytes

          byte[] getJMSCorrelationIDAsBytes()
                                     throws JMSException

      Gets the correlation ID as an array of bytes for the message.
      The use of a `byte[]` value for `JMSCorrelationID` is non-portable.

      Returns:
      the correlation ID of a message as an array of bytes

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the correlation ID due to some internal error.

      See Also:
      `Message.setJMSCorrelationID(String)`, `Message.getJMSCorrelationID()`, `Message.setJMSCorrelationIDAsBytes(byte[])`

    <!-- -->

    - #### setJMSCorrelationIDAsBytes

          void setJMSCorrelationIDAsBytes(byte[] correlationID)
                                   throws JMSException

      Sets the correlation ID as an array of bytes for the message.
      The array is copied before the method returns, so future modifications to the array will not alter this message header.

      If a provider supports the native concept of correlation ID, a JMS client may need to assign specific `JMSCorrelationID` values to match those expected by native messaging clients. JMS providers without native correlation ID values are not required to support this method and its corresponding get method; their implementation may throw a `java.lang.UnsupportedOperationException`.

      The use of a `byte[]` value for `JMSCorrelationID` is non-portable.

      Parameters:
      `correlationID` - the correlation ID value as an array of bytes

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the correlation ID due to some internal error.

      See Also:
      `Message.setJMSCorrelationID(String)`, `Message.getJMSCorrelationID()`, `Message.getJMSCorrelationIDAsBytes()`

    <!-- -->

    - #### setJMSCorrelationID

          void setJMSCorrelationID(java.lang.String correlationID)
                            throws JMSException

      Sets the correlation ID for the message.
      A client can use the `JMSCorrelationID` header field to link one message with another. A typical use is to link a response message with its request message.

      `JMSCorrelationID` can hold one of the following:

      - A provider-specific message ID
      - An application-specific `String`
      - A provider-native `byte[]` value

      Since each message sent by a JMS provider is assigned a message ID value, it is convenient to link messages via message ID. All message ID values must start with the `'ID:'` prefix.

      In some cases, an application (made up of several clients) needs to use an application-specific value for linking messages. For instance, an application may use `JMSCorrelationID` to hold a value referencing some external information. Application-specified values must not start with the `'ID:'` prefix; this is reserved for provider-generated message ID values.

      If a provider supports the native concept of correlation ID, a JMS client may need to assign specific `JMSCorrelationID` values to match those expected by clients that do not use the JMS API. A `byte[]` value is used for this purpose. JMS providers without native correlation ID values are not required to support `byte[]` values. The use of a `byte[]` value for `JMSCorrelationID` is non-portable.

      Parameters:
      `correlationID` - the message ID of a message being referred to

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the correlation ID due to some internal error.

      See Also:
      `Message.getJMSCorrelationID()`, `Message.getJMSCorrelationIDAsBytes()`, `Message.setJMSCorrelationIDAsBytes(byte[])`

    <!-- -->

    - #### getJMSCorrelationID

          java.lang.String getJMSCorrelationID()
                                        throws JMSException

      Gets the correlation ID for the message.
      This method is used to return correlation ID values that are either provider-specific message IDs or application-specific `String` values.

      Returns:
      the correlation ID of a message as a `String`

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the correlation ID due to some internal error.

      See Also:
      `Message.setJMSCorrelationID(String)`, `Message.getJMSCorrelationIDAsBytes()`, `Message.setJMSCorrelationIDAsBytes(byte[])`

    <!-- -->

    - #### getJMSReplyTo

          Destination getJMSReplyTo()
                             throws JMSException

      Gets the `Destination` object to which a reply to this message should be sent.
      Returns:
      `Destination` to which to send a response to this message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the `JMSReplyTo` destination due to some internal error.

      See Also:
      `Message.setJMSReplyTo(Destination)`

    <!-- -->

    - #### setJMSReplyTo

          void setJMSReplyTo(Destination replyTo)
                      throws JMSException

      Sets the `Destination` object to which a reply to this message should be sent.
      The `JMSReplyTo` header field contains the destination where a reply to the current message should be sent. If it is null, no reply is expected. The destination may be either a `Queue` object or a `Topic` object.

      Messages sent with a null `JMSReplyTo` value may be a notification of some event, or they may just be some data the sender thinks is of interest.

      Messages with a `JMSReplyTo` value typically expect a response. A response is optional; it is up to the client to decide. These messages are called requests. A message sent in response to a request is called a reply.

      In some cases a client may wish to match a request it sent earlier with a reply it has just received. The client can use the `JMSCorrelationID` header field for this purpose.

      Parameters:
      `replyTo` - `Destination` to which to send a response to this message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the `JMSReplyTo` destination due to some internal error.

      See Also:
      `Message.getJMSReplyTo()`

    <!-- -->

    - #### getJMSDestination

          Destination getJMSDestination()
                                 throws JMSException

      Gets the `Destination` object for this message.
      The `JMSDestination` header field contains the destination to which the message is being sent.

      When a message is sent, this field is ignored. After completion of the `send` or `publish` method, the field holds the destination specified by the method.

      When a message is received, its `JMSDestination` value must be equivalent to the value assigned when it was sent.

      Returns:
      the destination of this message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the destination due to some internal error.

      See Also:
      `Message.setJMSDestination(Destination)`

    <!-- -->

    - #### setJMSDestination

          void setJMSDestination(Destination destination)
                          throws JMSException

      Sets the `Destination` object for this message.
      JMS providers set this field when a message is sent. This method can be used to change the value for a message that has been received.

      Parameters:
      `destination` - the destination for this message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the destination due to some internal error.

      See Also:
      `Message.getJMSDestination()`

    <!-- -->

    - #### getJMSDeliveryMode

          int getJMSDeliveryMode()
                          throws JMSException

      Gets the `DeliveryMode` value specified for this message.
      Returns:
      the delivery mode for this message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the delivery mode due to some internal error.

      See Also:
      `Message.setJMSDeliveryMode(int)`, [`DeliveryMode`](DeliveryMode.md)

    <!-- -->

    - #### setJMSDeliveryMode

          void setJMSDeliveryMode(int deliveryMode)
                           throws JMSException

      Sets the `DeliveryMode` value for this message.
      JMS providers set this field when a message is sent. This method can be used to change the value for a message that has been received.

      Parameters:
      `deliveryMode` - the delivery mode for this message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the delivery mode due to some internal error.

      See Also:
      `Message.getJMSDeliveryMode()`, [`DeliveryMode`](DeliveryMode.md)

    <!-- -->

    - #### getJMSRedelivered

          boolean getJMSRedelivered()
                             throws JMSException

      Gets an indication of whether this message is being redelivered.
      If a client receives a message with the `JMSRedelivered` field set, it is likely, but not guaranteed, that this message was delivered earlier but that its receipt was not acknowledged at that time.

      Returns:
      true if this message is being redelivered

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the redelivered state due to some internal error.

      See Also:
      `Message.setJMSRedelivered(boolean)`

    <!-- -->

    - #### setJMSRedelivered

          void setJMSRedelivered(boolean redelivered)
                          throws JMSException

      Specifies whether this message is being redelivered.
      This field is set at the time the message is delivered. This method can be used to change the value for a message that has been received.

      Parameters:
      `redelivered` - an indication of whether this message is being redelivered

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the redelivered state due to some internal error.

      See Also:
      `Message.getJMSRedelivered()`

    <!-- -->

    - #### getJMSType

          java.lang.String getJMSType()
                               throws JMSException

      Gets the message type identifier supplied by the client when the message was sent.
      Returns:
      the message type

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the message type due to some internal error.

      See Also:
      `Message.setJMSType(String)`

    <!-- -->

    - #### setJMSType

          void setJMSType(java.lang.String type)
                   throws JMSException

      Sets the message type.
      Some JMS providers use a message repository that contains the definitions of messages sent by applications. The `JMSType` header field may reference a message's definition in the provider's repository.

      The JMS API does not define a standard message definition repository, nor does it define a naming policy for the definitions it contains.

      Some messaging systems require that a message type definition for each application message be created and that each message specify its type. In order to work with such JMS providers, JMS clients should assign a value to `JMSType`, whether the application makes use of it or not. This ensures that the field is properly set for those providers that require it.

      To ensure portability, JMS clients should use symbolic values for `JMSType` that can be configured at installation time to the values defined in the current provider's message repository. If string literals are used, they may not be valid type names for some JMS providers.

      Parameters:
      `type` - the message type

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the message type due to some internal error.

      See Also:
      `Message.getJMSType()`

    <!-- -->

    - #### getJMSExpiration

          long getJMSExpiration()
                         throws JMSException

      Gets the message's expiration value.
      When a message is sent, the `JMSExpiration` header field is left unassigned. After completion of the `send` or `publish` method, it holds the expiration time of the message. This is the sum of the time-to-live value specified by the client and the GMT at the time of the `send` or `publish`.

      If the time-to-live is specified as zero, `JMSExpiration` is set to zero to indicate that the message does not expire.

      When a message's expiration time is reached, a provider should discard it. The JMS API does not define any form of notification of message expiration.

      Clients should not receive messages that have expired; however, the JMS API does not guarantee that this will not happen.

      Returns:
      the time the message expires, which is the sum of the time-to-live value specified by the client and the GMT at the time of the send

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the message expiration due to some internal error.

      See Also:
      `Message.setJMSExpiration(long)`

    <!-- -->

    - #### setJMSExpiration

          void setJMSExpiration(long expiration)
                         throws JMSException

      Sets the message's expiration value.
      JMS providers set this field when a message is sent. This method can be used to change the value for a message that has been received.

      Parameters:
      `expiration` - the message's expiration time

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the message expiration due to some internal error.

      See Also:
      `Message.getJMSExpiration()`

    <!-- -->

    - #### getJMSPriority

          int getJMSPriority()
                      throws JMSException

      Gets the message priority level.
      The JMS API defines ten levels of priority value, with 0 as the lowest priority and 9 as the highest. In addition, clients should consider priorities 0-4 as gradations of normal priority and priorities 5-9 as gradations of expedited priority.

      The JMS API does not require that a provider strictly implement priority ordering of messages; however, it should do its best to deliver expedited messages ahead of normal messages.

      Returns:
      the default message priority

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the message priority due to some internal error.

      See Also:
      `Message.setJMSPriority(int)`

    <!-- -->

    - #### setJMSPriority

          void setJMSPriority(int priority)
                       throws JMSException

      Sets the priority level for this message.
      JMS providers set this field when a message is sent. This method can be used to change the value for a message that has been received.

      Parameters:
      `priority` - the priority of this message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the message priority due to some internal error.

      See Also:
      `Message.getJMSPriority()`

    <!-- -->

    - #### clearProperties

          void clearProperties()
                        throws JMSException

      Clears a message's properties.
      The message's header fields and body are not cleared.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to clear the message properties due to some internal error.

    <!-- -->

    - #### propertyExists

          boolean propertyExists(java.lang.String name)
                          throws JMSException

      Indicates whether a property value exists.
      Parameters:
      `name` - the name of the property to test

      Returns:
      true if the property exists

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to determine if the property exists due to some internal error.

    <!-- -->

    - #### getBooleanProperty

          boolean getBooleanProperty(java.lang.String name)
                              throws JMSException

      Returns the value of the `boolean` property with the specified name.
      Parameters:
      `name` - the name of the `boolean` property

      Returns:
      the `boolean` property value for the specified name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the property value due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getByteProperty

          byte getByteProperty(java.lang.String name)
                        throws JMSException

      Returns the value of the `byte` property with the specified name.
      Parameters:
      `name` - the name of the `byte` property

      Returns:
      the `byte` property value for the specified name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the property value due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getShortProperty

          short getShortProperty(java.lang.String name)
                          throws JMSException

      Returns the value of the `short` property with the specified name.
      Parameters:
      `name` - the name of the `short` property

      Returns:
      the `short` property value for the specified name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the property value due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getIntProperty

          int getIntProperty(java.lang.String name)
                      throws JMSException

      Returns the value of the `int` property with the specified name.
      Parameters:
      `name` - the name of the `int` property

      Returns:
      the `int` property value for the specified name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the property value due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getLongProperty

          long getLongProperty(java.lang.String name)
                        throws JMSException

      Returns the value of the `long` property with the specified name.
      Parameters:
      `name` - the name of the `long` property

      Returns:
      the `long` property value for the specified name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the property value due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getFloatProperty

          float getFloatProperty(java.lang.String name)
                          throws JMSException

      Returns the value of the `float` property with the specified name.
      Parameters:
      `name` - the name of the `float` property

      Returns:
      the `float` property value for the specified name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the property value due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getDoubleProperty

          double getDoubleProperty(java.lang.String name)
                            throws JMSException

      Returns the value of the `double` property with the specified name.
      Parameters:
      `name` - the name of the `double` property

      Returns:
      the `double` property value for the specified name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the property value due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getStringProperty

          java.lang.String getStringProperty(java.lang.String name)
                                      throws JMSException

      Returns the value of the `String` property with the specified name.
      Parameters:
      `name` - the name of the `String` property

      Returns:
      the `String` property value for the specified name; if there is no property by this name, a null value is returned

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the property value due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if this type conversion is invalid.

    <!-- -->

    - #### getObjectProperty

          java.lang.Object getObjectProperty(java.lang.String name)
                                      throws JMSException

      Returns the value of the Java object property with the specified name.
      This method can be used to return, in objectified format, an object that has been stored as a property in the message with the equivalent `setObjectProperty` method call, or its equivalent primitive `set`*`type`*`Property` method.

      Parameters:
      `name` - the name of the Java object property

      Returns:
      the Java object property value with the specified name, in objectified format (for example, if the property was set as an `int`, an `Integer` is returned); if there is no property by this name, a null value is returned

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the property value due to some internal error.

    <!-- -->

    - #### getPropertyNames

          java.util.Enumeration getPropertyNames()
                                          throws JMSException

      Returns an `Enumeration` of all the property names.
      Note that JMS standard header fields are not considered properties and are not returned in this enumeration.

      Returns:
      an enumeration of all the names of property values

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the property names due to some internal error.

    <!-- -->

    - #### setBooleanProperty

          void setBooleanProperty(java.lang.String name,
                                  boolean value)
                           throws JMSException

      Sets a `boolean` property value with the specified name into the message.
      Parameters:
      `name` - the name of the `boolean` property

      `value` - the `boolean` property value to set

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the property due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setByteProperty

          void setByteProperty(java.lang.String name,
                               byte value)
                        throws JMSException

      Sets a `byte` property value with the specified name into the message.
      Parameters:
      `name` - the name of the `byte` property

      `value` - the `byte` property value to set

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the property due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setShortProperty

          void setShortProperty(java.lang.String name,
                                short value)
                         throws JMSException

      Sets a `short` property value with the specified name into the message.
      Parameters:
      `name` - the name of the `short` property

      `value` - the `short` property value to set

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the property due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setIntProperty

          void setIntProperty(java.lang.String name,
                              int value)
                       throws JMSException

      Sets an `int` property value with the specified name into the message.
      Parameters:
      `name` - the name of the `int` property

      `value` - the `int` property value to set

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the property due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setLongProperty

          void setLongProperty(java.lang.String name,
                               long value)
                        throws JMSException

      Sets a `long` property value with the specified name into the message.
      Parameters:
      `name` - the name of the `long` property

      `value` - the `long` property value to set

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the property due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setFloatProperty

          void setFloatProperty(java.lang.String name,
                                float value)
                         throws JMSException

      Sets a `float` property value with the specified name into the message.
      Parameters:
      `name` - the name of the `float` property

      `value` - the `float` property value to set

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the property due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setDoubleProperty

          void setDoubleProperty(java.lang.String name,
                                 double value)
                          throws JMSException

      Sets a `double` property value with the specified name into the message.
      Parameters:
      `name` - the name of the `double` property

      `value` - the `double` property value to set

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the property due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setStringProperty

          void setStringProperty(java.lang.String name,
                                 java.lang.String value)
                          throws JMSException

      Sets a `String` property value with the specified name into the message.
      Parameters:
      `name` - the name of the `String` property

      `value` - the `String` property value to set

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the property due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### setObjectProperty

          void setObjectProperty(java.lang.String name,
                                 java.lang.Object value)
                          throws JMSException

      Sets a Java object property value with the specified name into the message.
      Note that this method works only for the objectified primitive object types (`Integer`, `Double`, `Long` ...) and `String` objects.

      Parameters:
      `name` - the name of the Java object property

      `value` - the Java object property value to set

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the property due to some internal error.

      `java.lang.IllegalArgumentException` - if the name is null or if the name is an empty string.

      [`MessageFormatException`](MessageFormatException.md) - if the object is invalid

      [`MessageNotWriteableException`](MessageNotWriteableException.md) - if properties are read-only

    <!-- -->

    - #### acknowledge

          void acknowledge()
                    throws JMSException

      Acknowledges all consumed messages of the session of this consumed message.
      All consumed JMS messages support the `acknowledge` method for use when a client has specified that its JMS session's consumed messages are to be explicitly acknowledged. By invoking `acknowledge` on a consumed message, a client acknowledges all messages consumed by the session that the message was delivered to.

      Calls to `acknowledge` are ignored for both transacted sessions and sessions specified to use implicit acknowledgement modes.

      A client may individually acknowledge each message as it is consumed, or it may choose to acknowledge messages as an application-defined group (which is done by calling acknowledge on the last received message of the group, thereby acknowledging all messages consumed by the session.)

      Messages that have been received but not acknowledged may be redelivered.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to acknowledge the messages due to some internal error.

      [`IllegalStateException`](IllegalStateException.md) - if this method is called on a closed session.

      See Also:
      [`Session.CLIENT_ACKNOWLEDGE`](Session.md)

    <!-- -->

    - #### clearBody

          void clearBody()
                  throws JMSException

      Clears out the message body. Clearing a message's body does not clear its header values or property entries.
      If this message body was read-only, calling this method leaves the message body in the same state as an empty body in a newly created message.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to clear the message body due to some internal error.

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

- [Prev Class](MapMessage.md)
- [Next Class](MessageConsumer.md)

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
