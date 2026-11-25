Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQDequeueOptions.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQAgent.md)
- [Next Class](AQDequeueOptions.DeliveryFilter.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.jdbc.aq

## Class AQDequeueOptions

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.aq.AQDequeueOptions

<!-- -->

-

  ------------------------------------------------------------------------



      public class AQDequeueOptions
      extends Object

  Specifies the options available for the dequeue operation.

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                        |
    |-------------------|------------------------------------------------------------------------------|
    | `static class `   | [`AQDequeueOptions.DeliveryFilter`](AQDequeueOptions.DeliveryFilter.md)      |
    | `static class `   | [`AQDequeueOptions.DequeueMode`](AQDequeueOptions.DequeueMode.md)            |
    | `static class `   | [`AQDequeueOptions.NavigationOption`](AQDequeueOptions.NavigationOption.md)  |
    | `static class `   | [`AQDequeueOptions.VisibilityOption`](AQDequeueOptions.VisibilityOption.md)  |

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                              |
    |-------------------|--------------------------------------------------------------------|
    | `static int`      | `DEQUEUE_NO_WAIT`                                                  |
    | `static int`      | `DEQUEUE_WAIT_FOREVER`                                             |
    | `static int`      | `MAX_RAW_PAYLOAD`<br>Default maximum buffer size of a RAW payload. |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                       |
    |-------------------------------------------------------------------|
    | `AQDequeueOptions``()`<br>Constructs the default dequeue options. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                                                                                                              |
    |-------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getCondition``()`<br>Returns the dequeue condition.                                                                                                                                                                                                |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getConsumerName``()`<br>Returns the consumer name.                                                                                                                                                                                                 |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getCorrelation``()`<br>Returns the correlation criterion.                                                                                                                                                                                          |
    | [`AQDequeueOptions.DeliveryFilter`](AQDequeueOptions.DeliveryFilter.md)                         | `getDeliveryFilter``()`<br>Returns the delivery option.                                                                                                                                                                                             |
    | `byte[]`                                                                                        | `getDequeueMessageId``()`<br>Returns the message id of the message the be dequeued.                                                                                                                                                                 |
    | [`AQDequeueOptions.DequeueMode`](AQDequeueOptions.DequeueMode.md)                               | `getDequeueMode``()`<br>Returns the dequeue mode.                                                                                                                                                                                                   |
    | `int`                                                                                           | `getMaximumBufferLength``()`<br>Returns the max buffer size for RAW queues.                                                                                                                                                                         |
    | [`AQDequeueOptions.NavigationOption`](AQDequeueOptions.NavigationOption.md)                     | `getNavigation``()`<br>Returns the position criterion.                                                                                                                                                                                              |
    | `boolean`                                                                                       | `getRetrieveMessageId``()`<br>Returns the value of the option that can be set to force the server to return the id of the message during dequeue.                                                                                                   |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getTransformation``()`<br>Returns the value of transformation option.                                                                                                                                                                              |
    | [`AQDequeueOptions.VisibilityOption`](AQDequeueOptions.VisibilityOption.md)                     | `getVisibility``()`<br>Returns the visibility parameter.                                                                                                                                                                                            |
    | `int`                                                                                           | `getWait``()`<br>Returns the wait option.                                                                                                                                                                                                           |
    | `void`                                                                                          | `setCondition``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _condition)`<br>Sets a conditional expression based on the message properties, the message data properties, and PL/SQL functions. |
    | `void`                                                                                          | `setConsumerName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` consumerName)`<br>Specifies a consumer name.                                                                                   |
    | `void`                                                                                          | `setCorrelation``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` correlation)`<br>Specifies a correlation criterion (or search criterion) for the dequeue operation.                             |
    | `void`                                                                                          | `setDeliveryFilter``(`[`AQDequeueOptions.DeliveryFilter`](AQDequeueOptions.DeliveryFilter.md)` delivery)`<br>Use this method to dequeue buffered messages only, persistent messages only or both.                                                   |
    | `void`                                                                                          | `setDequeueMessageId``(byte[] deqMsgId)`<br>Specifies the message identifier of the message to be dequeued.                                                                                                                                         |
    | `void`                                                                                          | `setDequeueMode``(`[`AQDequeueOptions.DequeueMode`](AQDequeueOptions.DequeueMode.md)` deqMode)`<br>Specifies the locking behavior associated with the dequeue operation.                                                                            |
    | `void`                                                                                          | `setMaximumBufferLength``(int length)`<br>Sets the maximum number of bytes that will be allocated when dequeueing a message from a RAW queue.                                                                                                       |
    | `void`                                                                                          | `setNavigation``(`[`AQDequeueOptions.NavigationOption`](AQDequeueOptions.NavigationOption.md)` navigation)`<br>Specifies the position of the message that will be retrieved.                                                                        |
    | `void`                                                                                          | `setRetrieveMessageId``(boolean retrieveIt)`<br>Set this to true in order to retrieve the message id during dequeue.                                                                                                                                |
    | `void`                                                                                          | `setTransformation``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _transformation)`<br>Specifies a transformation that will be applied after dequeuing the message.                            |
    | `void`                                                                                          | `setVisibility``(`[`AQDequeueOptions.VisibilityOption`](AQDequeueOptions.VisibilityOption.md)` visibility)`<br>Specifies whether the message is dequeued as part of the current transaction.                                                        |
    | `void`                                                                                          | `setWait``(int wait)`<br>Specifies the wait time if there is currently no message available which matches the search criterion.                                                                                                                     |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Field Detail

    - #### DEQUEUE_WAIT_FOREVER

          public static final int DEQUEUE_WAIT_FOREVER

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DEQUEUE_NO_WAIT

          public static final int DEQUEUE_NO_WAIT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MAX_RAW_PAYLOAD

          public static final int MAX_RAW_PAYLOAD

      Default maximum buffer size of a RAW payload.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### AQDequeueOptions

          public AQDequeueOptions()

      Constructs the default dequeue options.

  <!-- -->

  - ### Method Detail

    - #### setConsumerName

          public void setConsumerName(String consumerName)
                               throws SQLException

      Specifies a consumer name. Only those messages matching the consumer name are accessed. If a queue is not set up for multiple consumers, this field should be set to null.
      Parameters:
      `consumerName` - the consumer name

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConsumerName

          public String getConsumerName()

      Returns the consumer name.
      See Also:
      `setConsumerName(String)`

    <!-- -->

    - #### setCorrelation

          public void setCorrelation(String correlation)
                              throws SQLException

      Specifies a correlation criterion (or search criterion) for the dequeue operation. Special pattern matching characters, such as the percent sign (%) and the underscore (\_) can be used. If more than one message satisfies the pattern, the order of dequeuing is undetermined.
      For example, if you want to dequeue only messages whose correlation identifier starts with an upper-case "W.", you would set the correlation criterion to:

                 dequeueOptions.setCorrelation("W%");


      Parameters:
      `correlation` - the correlation criterion

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getCorrelation

          public String getCorrelation()

      Returns the correlation criterion.
      See Also:
      `setCorrelation(String)`

    <!-- -->

    - #### setDequeueMode

          public void setDequeueMode(AQDequeueOptions.DequeueMode deqMode)
                              throws SQLException

      Specifies the locking behavior associated with the dequeue operation.
      Parameters:
      `deqMode` - The only valid dequeue modes are:

      - `DequeueMode.BROWSE`
      - `DequeueMode.LOCKED`
      - `DequeueMode.REMOVE`
      - `DequeueMode.REMOVE_NODATA`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDequeueMode

          public AQDequeueOptions.DequeueMode getDequeueMode()

      Returns the dequeue mode.
      See Also:
      `setDequeueMode(DequeueMode)`

    <!-- -->

    - #### setDequeueMessageId

          public void setDequeueMessageId(byte[] deqMsgId)
                                   throws SQLException

      Specifies the message identifier of the message to be dequeued. This can be used to dequeue a unique message whose id is known.
      Parameters:
      `deqMsgId` - message identifier. Can be 'null' to disable dequeue based on a particular message id.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDequeueMessageId

          public byte[] getDequeueMessageId()

      Returns the message id of the message the be dequeued. If 'null', then the dequeue operation will not be based on a particular message id.
      See Also:
      `setDequeueMessageId(byte[])`

    <!-- -->

    - #### setNavigation

          public void setNavigation(AQDequeueOptions.NavigationOption navigation)
                             throws SQLException

      Specifies the position of the message that will be retrieved. First, the position is determined. Second, the search criterion is applied. Finally, the message is retrieved.
      The default behavior is to retrieve the next message which is available and matches the seatch criterion.

      Parameters:
      `navigation` - The position criterion can be any of the following:

      - NavigationOption.FIRST_MESSAGE
      - NavigationOption.NEXT_MESSAGE
      - NavigationOption.NEXT_TRANSACTION

      `navigation` - the position criterion

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getNavigation

          public AQDequeueOptions.NavigationOption getNavigation()

      Returns the position criterion.
      See Also:
      `setNavigation(NavigationOption)`

    <!-- -->

    - #### setVisibility

          public void setVisibility(AQDequeueOptions.VisibilityOption visibility)
                             throws SQLException

      Specifies whether the message is dequeued as part of the current transaction. The visibility parameter is ignored when using the BROWSE mode.
      Parameters:
      `visibility` - can be:

      - VisibilityOption.ON_COMMIT
      - VisibilityOption.IMMEDIATE

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getVisibility

          public AQDequeueOptions.VisibilityOption getVisibility()

      Returns the visibility parameter.
      See Also:
      `setVisibility(VisibilityOption)`

    <!-- -->

    - #### setWait

          public void setWait(int wait)
                       throws SQLException

      Specifies the wait time if there is currently no message available which matches the search criterion. This parameter is ignored if messages in the same group are being dequeued.
      Valid Values : Any int, but the following predefined constants are provided:

      - DEQUEUE_WAIT_FOREVER ( = -1) - wait forever. This is the default.
      - DEQUEUE_NO_WAIT ( = 0) - do not wait.

      If you use `DEQUEUE_WAIT_FOREVER` the dequeue operation will not return until a message which mathces the seach criterion is available in the queue. You can however interrupt the dequeue operation by calling `connection.cancel();`.

      Parameters:
      `wait` - the wait option

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getWait

          public int getWait()

      Returns the wait option.
      See Also:
      `setWait(int)`

    <!-- -->

    - #### setMaximumBufferLength

          public void setMaximumBufferLength(int length)
                                      throws SQLException

      Sets the maximum number of bytes that will be allocated when dequeueing a message from a RAW queue. The default maximum is DEFAULT_MAX_PAYLOAD_LENGTH but it can be changed to any other non zero value. This is to avoid allocating a huge buffer knowing that a message from a RAW queue can contain up to 4G bytes. If the buffer is not large enough to contain the entire message, the exceeding bytes will be silently ignored.
      Parameters:
      `length` - the max buffer size

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaximumBufferLength

          public int getMaximumBufferLength()

      Returns the max buffer size for RAW queues.
      See Also:
      `setMaximumBufferLength(int)`

    <!-- -->

    - #### setDeliveryFilter

          public void setDeliveryFilter(AQDequeueOptions.DeliveryFilter delivery)
                                 throws SQLException

      Use this method to dequeue buffered messages only, persistent messages only or both. By default the dequeue method will dequeue persistent messages only.
      Possible valid options are:

      - DeliveryFilter.PERSISTENT - to dequeue persistent messages only (this is the default).
      - DeliveryFilter.BUFFERED - to dequeue buffered messages only.
      - DeliveryFilter.PERSISTENT_OR_BUFFERED - to dequeue buffered or persistent messages.

      Parameters:
      `delivery` - the delivery options

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDeliveryFilter

          public AQDequeueOptions.DeliveryFilter getDeliveryFilter()

      Returns the delivery option.
      See Also:
      `setDeliveryFilter(oracle.jdbc.aq.AQDequeueOptions.DeliveryFilter)`

    <!-- -->

    - #### setRetrieveMessageId

          public void setRetrieveMessageId(boolean retrieveIt)

      Set this to true in order to retrieve the message id during dequeue. By default the server won't return the message id.
      Parameters:
      `retrieveIt` - retrieve message id or not?

    <!-- -->

    - #### getRetrieveMessageId

          public boolean getRetrieveMessageId()

      Returns the value of the option that can be set to force the server to return the id of the message during dequeue.
      See Also:
      `setRetrieveMessageId(boolean)`

    <!-- -->

    - #### setTransformation

          public void setTransformation(String _transformation)

      Specifies a transformation that will be applied after dequeuing the message. The source type of the transformation must match the type of the queue.
      Transformations must be created in PLSQL using `DBMS_TRANSFORM.CREATE_TRANSFORMATION(...)`.

      For example if the transformation 'OBJ2XML' has been created under the schema 'SCOTT' then it can be specified in the dequeue option with `dequeueOption.setTransformation("SCOTT.OBJ2XML")`.

      Parameters:
      `_transformation` - the transformation

    <!-- -->

    - #### getTransformation

          public String getTransformation()

      Returns the value of transformation option.
      See Also:
      `setTransformation(String)`

    <!-- -->

    - #### setCondition

          public void setCondition(String _condition)

      Sets a conditional expression based on the message properties, the message data properties, and PL/SQL functions.
      A dequeue condition is specified as a Boolean expression using syntax similar to the WHERE clause of a SQL query. This Boolean expression can include conditions on message properties, user data properties (object payloads only), and PL/SQL or SQL functions (as specified in the WHERE clause of a SQL query). Message properties include priority, corrid and other columns in the queue table

      To specify dequeue conditions on a message payload (object payload), use attributes of the object type in clauses. You must prefix each attribute with tab.user_data as a qualifier to indicate the specific column of the queue table that stores the payload. The dequeue condition parameter cannot exceed 4000 characters. If more than one message satisfies the dequeue condition, then the order of dequeuing is undetermined.

      Parameters:
      `_condition` - the dequeue condition

    <!-- -->

    - #### getCondition

          public String getCondition()

      Returns the dequeue condition.
      See Also:
      `setCondition(String)`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQDequeueOptions.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQAgent.md)
- [Next Class](AQDequeueOptions.DeliveryFilter.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
