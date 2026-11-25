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

- [Prev Class](TransactionInProgressException.md)
- [Next Class](XAConnection.md)

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

## Class TransactionRolledBackException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - [javax.jms.JMSException](JMSException.md)

      - - javax.jms.TransactionRolledBackException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class TransactionRolledBackException
      extends JMSException

  This exception must be thrown when a call to `Session.commit` results in a rollback of the current transaction.

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                        |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `TransactionRolledBackException``(java.lang.String reason)`<br>Constructs a `TransactionRolledBackException` with the specified reason.                                            |
    | `TransactionRolledBackException``(java.lang.String reason, java.lang.String errorCode)`<br>Constructs a `TransactionRolledBackException` with the specified reason and error code. |

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

    - #### TransactionRolledBackException

          public TransactionRolledBackException(java.lang.String reason,
                                                java.lang.String errorCode)

      Constructs a `TransactionRolledBackException` with the specified reason and error code.
      Parameters:
      `reason` - a description of the exception

      `errorCode` - a string specifying the vendor-specific error code

    <!-- -->

    - #### TransactionRolledBackException

          public TransactionRolledBackException(java.lang.String reason)

      Constructs a `TransactionRolledBackException` with the specified reason. The error code defaults to null.
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

- [Prev Class](TransactionInProgressException.md)
- [Next Class](XAConnection.md)

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
