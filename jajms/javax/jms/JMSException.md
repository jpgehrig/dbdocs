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

- [Prev Class](InvalidSelectorException.md)
- [Next Class](JMSSecurityException.md)

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

## Class JMSException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - javax.jms.JMSException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  <!-- -->

  Direct Known Subclasses:
  [AQjmsException](../../oracle/jms/AQjmsException.md), [AQjmsParseException](../../oracle/jms/AQjmsParseException.md), [IllegalStateException](IllegalStateException.md), [InvalidClientIDException](InvalidClientIDException.md), [InvalidDestinationException](InvalidDestinationException.md), [InvalidSelectorException](InvalidSelectorException.md), [JMSSecurityException](JMSSecurityException.md), [MessageEOFException](MessageEOFException.md), [MessageFormatException](MessageFormatException.md), [MessageNotReadableException](MessageNotReadableException.md), [MessageNotWriteableException](MessageNotWriteableException.md), [ResourceAllocationException](ResourceAllocationException.md), [TransactionInProgressException](TransactionInProgressException.md), [TransactionRolledBackException](TransactionRolledBackException.md)

  ------------------------------------------------------------------------



      public class JMSException
      extends java.lang.Exception

  This is the root class of all JMS API exceptions.

  It provides the following information:

  - A provider-specific string describing the error. This string is the standard exception message and is available via the `getMessage` method.
  - A provider-specific string error code
  - A reference to another exception. Often a JMS API exception will be the result of a lower-level problem. If appropriate, this lower-level exception can be linked to the JMS API exception.

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                    |
    |------------------------------------------------------------------------------------------------------------------------------------------------|
    | `JMSException``(java.lang.String reason)`<br>Constructs a `JMSException` with the specified reason and with the error code defaulting to null. |
    | `JMSException``(java.lang.String reason, java.lang.String errorCode)`<br>Constructs a `JMSException` with the specified reason and error code. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                       |
    |-----------------------|------------------------------------------------------------------------------|
    | `java.lang.String`    | `getErrorCode``()`<br>Gets the vendor-specific error code.                   |
    | `java.lang.Exception` | `getLinkedException``()`<br>Gets the exception linked to this one.           |
    | `void`                | `setLinkedException``(java.lang.Exception ex)`<br>Adds a linked `Exception`. |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### JMSException

          public JMSException(java.lang.String reason,
                              java.lang.String errorCode)

      Constructs a `JMSException` with the specified reason and error code.
      Parameters:
      `reason` - a description of the exception

      `errorCode` - a string specifying the vendor-specific error code

    <!-- -->

    - #### JMSException

          public JMSException(java.lang.String reason)

      Constructs a `JMSException` with the specified reason and with the error code defaulting to null.
      Parameters:
      `reason` - a description of the exception

  <!-- -->

  - ### Method Detail

    - #### getErrorCode

          public java.lang.String getErrorCode()

      Gets the vendor-specific error code.
      Returns:
      a string specifying the vendor-specific error code

    <!-- -->

    - #### getLinkedException

          public java.lang.Exception getLinkedException()

      Gets the exception linked to this one.
      Returns:
      the linked `Exception`, null if none

    <!-- -->

    - #### setLinkedException

          public void setLinkedException(java.lang.Exception ex)

      Adds a linked `Exception`.
      Parameters:
      `ex` - the linked `Exception`

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

- [Prev Class](InvalidSelectorException.md)
- [Next Class](JMSSecurityException.md)

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
