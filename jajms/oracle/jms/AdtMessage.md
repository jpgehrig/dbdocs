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
- [Next Class](AQjmsAdtMessage.md)

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

## Interface AdtMessage

- All Superinterfaces:
  [Message](../../javax/jms/Message.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsAdtMessage](AQjmsAdtMessage.md)

  ------------------------------------------------------------------------



      public interface AdtMessage
      extends Message

  Adds Oracle® Database Advanced Queuing extensions to `javax.jms.Message`.
  Allows use of the JMS api for messages stored in AQ queues containing Oracle ADT payloads.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Message](../../javax/jms/Message.md)

      [`DEFAULT_DELIVERY_MODE`](../../javax/jms/Message.md)`, `[`DEFAULT_PRIORITY`](../../javax/jms/Message.md)`, `[`DEFAULT_TIME_TO_LIVE`](../../javax/jms/Message.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                    |
    |--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `getAdtPayload``()`<br>Get the `CustomDatum`/`ORAData` object containing this Adt message's data **Important:** `CustomDatum` support will be deprecated in a future release.                                             |
    | `void`             | `setAdtPayload``(oracle.sql.CustomDatum payload)`<br>set the `CustomDatum` object containing this Adt message's data **Important:** `CustomDatum` support (and hence this method) will be deprecated in a future release. |
    | `void`             | `setAdtPayload``(oracle.jdbc.OracleData payload)`<br>set the `OracleData` object containing this Adt message's data                                                                                                       |
    | `void`             | `setAdtPayload``(oracle.sql.ORAData payload)`<br>set the `ORAData` object containing this Adt message's data                                                                                                              |

    - ### Methods inherited from interface javax.jms.[Message](../../javax/jms/Message.md)

      [`acknowledge`](../../javax/jms/Message.md)`, `[`clearBody`](../../javax/jms/Message.md)`, `[`clearProperties`](../../javax/jms/Message.md)`, `[`getBooleanProperty`](../../javax/jms/Message.md)`, `[`getByteProperty`](../../javax/jms/Message.md)`, `[`getDoubleProperty`](../../javax/jms/Message.md)`, `[`getFloatProperty`](../../javax/jms/Message.md)`, `[`getIntProperty`](../../javax/jms/Message.md)`, `[`getJMSCorrelationID`](../../javax/jms/Message.md)`, `[`getJMSCorrelationIDAsBytes`](../../javax/jms/Message.md)`, `[`getJMSDeliveryMode`](../../javax/jms/Message.md)`, `[`getJMSDestination`](../../javax/jms/Message.md)`, `[`getJMSExpiration`](../../javax/jms/Message.md)`, `[`getJMSMessageID`](../../javax/jms/Message.md)`, `[`getJMSPriority`](../../javax/jms/Message.md)`, `[`getJMSRedelivered`](../../javax/jms/Message.md)`, `[`getJMSReplyTo`](../../javax/jms/Message.md)`, `[`getJMSTimestamp`](../../javax/jms/Message.md)`, `[`getJMSType`](../../javax/jms/Message.md)`, `[`getLongProperty`](../../javax/jms/Message.md)`, `[`getObjectProperty`](../../javax/jms/Message.md)`, `[`getPropertyNames`](../../javax/jms/Message.md)`, `[`getShortProperty`](../../javax/jms/Message.md)`, `[`getStringProperty`](../../javax/jms/Message.md)`, `[`propertyExists`](../../javax/jms/Message.md)`, `[`setBooleanProperty`](../../javax/jms/Message.md)`, `[`setByteProperty`](../../javax/jms/Message.md)`, `[`setDoubleProperty`](../../javax/jms/Message.md)`, `[`setFloatProperty`](../../javax/jms/Message.md)`, `[`setIntProperty`](../../javax/jms/Message.md)`, `[`setJMSCorrelationID`](../../javax/jms/Message.md)`, `[`setJMSCorrelationIDAsBytes`](../../javax/jms/Message.md)`, `[`setJMSDeliveryMode`](../../javax/jms/Message.md)`, `[`setJMSDestination`](../../javax/jms/Message.md)`, `[`setJMSExpiration`](../../javax/jms/Message.md)`, `[`setJMSMessageID`](../../javax/jms/Message.md)`, `[`setJMSPriority`](../../javax/jms/Message.md)`, `[`setJMSRedelivered`](../../javax/jms/Message.md)`, `[`setJMSReplyTo`](../../javax/jms/Message.md)`, `[`setJMSTimestamp`](../../javax/jms/Message.md)`, `[`setJMSType`](../../javax/jms/Message.md)`, `[`setLongProperty`](../../javax/jms/Message.md)`, `[`setObjectProperty`](../../javax/jms/Message.md)`, `[`setShortProperty`](../../javax/jms/Message.md)`, `[`setStringProperty`](../../javax/jms/Message.md)

<!-- -->

- - ### Method Detail

    - #### setAdtPayload

          void setAdtPayload(oracle.sql.CustomDatum payload)
                      throws JMSException

      set the `CustomDatum` object containing this Adt message's data
      **Important:** `CustomDatum` support (and hence this method) will be deprecated in a future release.

      Use setAdtPayload (OracleData payload) instead.

      Parameters:
      `payload` - the message's data (the object must implement the `CustomDatum` interface). This payload must be a java object that represents the ADT that is defined as the queue/topic payload type

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the adt payload

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if message in read-only mode.

      See Also:
      `AdtMessage.setAdtPayload(OracleData)`

    <!-- -->

    - #### setAdtPayload

          void setAdtPayload(oracle.jdbc.OracleData payload)
                      throws JMSException

      set the `OracleData` object containing this Adt message's data
      Parameters:
      `payload` - the message's data (the object must implement the `ORAData` interface). This payload must be a java object that represents the ADT that is defined as the queue/topic payload type

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the adt payload

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if message in read-only mode.

    <!-- -->

    - #### setAdtPayload

          void setAdtPayload(oracle.sql.ORAData payload)
                      throws JMSException

      set the `ORAData` object containing this Adt message's data
      Parameters:
      `payload` - the message's data (the object must implement the `ORAData` interface). This payload must be a java object that represents the ADT that is defined as the queue/topic payload type

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to set the adt payload

      [`MessageNotWriteableException`](../../javax/jms/MessageNotWriteableException.md) - if message in read-only mode.

    <!-- -->

    - #### getAdtPayload

          java.lang.Object getAdtPayload()
                                  throws JMSException

      Get the `CustomDatum`/`ORAData` object containing this Adt message's data
      **Important:** `CustomDatum` support will be deprecated in a future release.

      Returns:
      the object containing this message's data

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get object due to some internal JMS error.

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
- [Next Class](AQjmsAdtMessage.md)

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
