Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQEnqueueOptions.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQDequeueOptions.VisibilityOption.md)
- [Next Class](AQEnqueueOptions.DeliveryMode.md)

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

## Class AQEnqueueOptions

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.aq.AQEnqueueOptions

<!-- -->

-

  ------------------------------------------------------------------------



      public class AQEnqueueOptions
      extends Object

  Specifies the options available for the enqueue operation.

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                      |
    |-------------------|--------------------------------------------------------------------------------------------|
    | `static class `   | [`AQEnqueueOptions.DeliveryMode`](AQEnqueueOptions.DeliveryMode.md)                        |
    | `static class `   | [`AQEnqueueOptions.SequenceDeviationOption`](AQEnqueueOptions.SequenceDeviationOption.md)  |
    | `static class `   | [`AQEnqueueOptions.VisibilityOption`](AQEnqueueOptions.VisibilityOption.md)                |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                      |
    |------------------------------------------------------------------|
    | `AQEnqueueOptions``()`<br>Construct the default enqueue options. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                                                                                    |
    |-------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`AQEnqueueOptions.DeliveryMode`](AQEnqueueOptions.DeliveryMode.md)                             | `getDeliveryMode``()`<br>Returns the delivery option.                                                                                                                                                                     |
    | `byte[]`                                                                                        | `getRelativeMessageId``()`<br>Returns the relative message id.                                                                                                                                                            |
    | `boolean`                                                                                       | `getRetrieveMessageId``()`<br>Returns the value of the enqueued message id option.                                                                                                                                        |
    | [`AQEnqueueOptions.SequenceDeviationOption`](AQEnqueueOptions.SequenceDeviationOption.md)       | `getSequenceDeviation``()`<br>Returns the sequence deviation.                                                                                                                                                             |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getTransformation``()`<br>Returns the value of transformation option.                                                                                                                                                    |
    | [`AQEnqueueOptions.VisibilityOption`](AQEnqueueOptions.VisibilityOption.md)                     | `getVisibility``()`<br>Returns the transactional behavior.                                                                                                                                                                |
    | `void`                                                                                          | `setDeliveryMode``(`[`AQEnqueueOptions.DeliveryMode`](AQEnqueueOptions.DeliveryMode.md)` delivery)`<br>Specifies the delivery mode: persistent or buffered.                                                               |
    | `void`                                                                                          | `setRelativeMessageId``(byte[] relativeMessageId)`<br>Deprecated.                                                                                                                                                         |
    | `void`                                                                                          | `setRetrieveMessageId``(boolean retrieveIt)`<br>Set this to true to retrieve the message id back from the server when the message has been enqueued.                                                                      |
    | `void`                                                                                          | `setSequenceDeviation``(`[`AQEnqueueOptions.SequenceDeviationOption`](AQEnqueueOptions.SequenceDeviationOption.md)` sequenceDeviation)`<br>Deprecated.                                                                    |
    | `void`                                                                                          | `setTransformation``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _transformation)`<br>Specifies a transformation that will be applied before enqueuing the message. |
    | `void`                                                                                          | `setVisibility``(`[`AQEnqueueOptions.VisibilityOption`](AQEnqueueOptions.VisibilityOption.md)` visibility)`<br>Specifies the transactional behavior of the enqueue request.                                               |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### AQEnqueueOptions

          public AQEnqueueOptions()

      Construct the default enqueue options.

  <!-- -->

  - ### Method Detail

    - #### setRelativeMessageId

          public void setRelativeMessageId(byte[] relativeMessageId)
                                    throws SQLException

      Deprecated. 
      Specifies the message identifier of the message which is referenced in the sequence deviation operation. This value is valid if and only if `SequenceDeviationOption.BEFORE` is specified in setSequenceDeviation and is ignored if the sequence deviation is not specified.
      This feature is deprecated and may be removed in a future release.

      Parameters:
      `relativeMessageId` - relative message id

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getRelativeMessageId

          public byte[] getRelativeMessageId()

      Returns the relative message id.
      See Also:
      `setRelativeMessageId(byte[])`

    <!-- -->

    - #### setSequenceDeviation

          public void setSequenceDeviation(AQEnqueueOptions.SequenceDeviationOption sequenceDeviation)
                                    throws SQLException

      Deprecated. 
      Specifies whether the message being enqueued should be dequeued before other message(s) already in the queue. This feature is deprecated for new applications, but it is retained for compatibility.
      Parameters:
      `sequenceDeviation` - the possible values are:

      - `SequenceDeviationOption.BOTTOM`
      - `SequenceDeviationOption.BEFORE`
      - `SequenceDeviationOption.TOP`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSequenceDeviation

          public AQEnqueueOptions.SequenceDeviationOption getSequenceDeviation()

      Returns the sequence deviation.
      See Also:
      `setSequenceDeviation(SequenceDeviationOption)`

    <!-- -->

    - #### setVisibility

          public void setVisibility(AQEnqueueOptions.VisibilityOption visibility)
                             throws SQLException

      Specifies the transactional behavior of the enqueue request.
      Parameters:
      `visibility` - The possible options are:

      - `ENQUEUE_ON_COMMIT`
      - `ENQUEUE_IMMEDIATE`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getVisibility

          public AQEnqueueOptions.VisibilityOption getVisibility()

      Returns the transactional behavior.
      See Also:
      `setVisibility(VisibilityOption)`

    <!-- -->

    - #### setDeliveryMode

          public void setDeliveryMode(AQEnqueueOptions.DeliveryMode delivery)
                               throws SQLException

      Specifies the delivery mode: persistent or buffered. Note that buffered message are more performant but persistent ones are safer.
      Possible values are:

      - ENQUEUE_BUFFERED - to enqueue a buffered message
      - ENQUEUE_PERSISTENT - to enqueue a persistent message. This is the default.

      Parameters:
      `delivery` - the delivery mode

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDeliveryMode

          public AQEnqueueOptions.DeliveryMode getDeliveryMode()

      Returns the delivery option.
      See Also:
      `setDeliveryMode(DeliveryMode)`

    <!-- -->

    - #### setRetrieveMessageId

          public void setRetrieveMessageId(boolean retrieveIt)

      Set this to true to retrieve the message id back from the server when the message has been enqueued.
      By default the message id won't be retrieved.

      Parameters:
      `retrieveIt` - the enqueued message id option

    <!-- -->

    - #### getRetrieveMessageId

          public boolean getRetrieveMessageId()

      Returns the value of the enqueued message id option.
      See Also:
      `setRetrieveMessageId(boolean)`

    <!-- -->

    - #### setTransformation

          public void setTransformation(String _transformation)

      Specifies a transformation that will be applied before enqueuing the message. The return type of the transformation function must match the type of the queue.
      Transformations must be created in PLSQL using `DBMS_TRANSFORM.CREATE_TRANSFORMATION(...)`.

      For example if the transformation 'OBJ2XML' has been created under the schema 'SCOTT' then it can be specified in the dequeue option with `enqueueOption.setTransformation("SCOTT.OBJ2XML")`.

      Parameters:
      `_transformation` - the transformation

    <!-- -->

    - #### getTransformation

          public String getTransformation()

      Returns the value of transformation option.
      See Also:
      `setTransformation(String)`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQEnqueueOptions.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQDequeueOptions.VisibilityOption.md)
- [Next Class](AQEnqueueOptions.DeliveryMode.md)

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
