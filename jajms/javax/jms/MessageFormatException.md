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

- [Prev Class](MessageEOFException.md)
- [Next Class](MessageListener.md)

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

## Class MessageFormatException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - [javax.jms.JMSException](JMSException.md)

      - - javax.jms.MessageFormatException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class MessageFormatException
      extends JMSException

  This exception must be thrown when a JMS client attempts to use a data type not supported by a message or attempts to read data in a message as the wrong type. It must also be thrown when equivalent type errors are made with message property values. For example, this exception must be thrown if `StreamMessage.writeObject` is given an unsupported class or if `StreamMessage.readShort` is used to read a `boolean` value. Note that the special case of a failure caused by an attempt to read improperly formatted `String` data as numeric values must throw the `java.lang.NumberFormatException`.

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                        |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `MessageFormatException``(java.lang.String reason)`<br>Constructs a `MessageFormatException` with the specified reason.                                            |
    | `MessageFormatException``(java.lang.String reason, java.lang.String errorCode)`<br>Constructs a `MessageFormatException` with the specified reason and error code. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class javax.jms.[JMSException](JMSException.md)

      [`getErrorCode`](JMSException.md)`, `[`getLinkedException`](JMSException.md)`, `[`setLinkedException`](JMSException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### MessageFormatException

          public MessageFormatException(java.lang.String reason,
                                        java.lang.String errorCode)

      Constructs a `MessageFormatException` with the specified reason and error code.
      Parameters:
      `reason` - a description of the exception

      `errorCode` - a string specifying the vendor-specific error code

    <!-- -->

    - #### MessageFormatException

          public MessageFormatException(java.lang.String reason)

      Constructs a `MessageFormatException` with the specified reason. The error code defaults to null.
      Parameters:
      `reason` - a description of the exception

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

- [Prev Class](MessageEOFException.md)
- [Next Class](MessageListener.md)

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
