Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](IncrementalChangeException.md)
- [Next Class](NotPreparedException.md)

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

oracle.olapi.transaction

## Class NotCommittableException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - [oracle.olapi.OLAPIException](../OLAPIException.md)

      - - oracle.olapi.transaction.NotCommittableException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class NotCommittableException
      extends OLAPIException

  Indicates that the `TransactionProvider` has determined that the query defined in the current `Transaction` is invalid and the `TransactionProvider` is therefore preventing the application from committing the `Transaction`.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                      |
    |--------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NotCommittableException``(java.lang.String message)`<br>Creates a `NotCommittableException` with the specified message.                         |
    | `NotCommittableException``(java.lang.String message, java.lang.String param)`<br>Creates a `NotCommittableException` with the specified message. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.olapi.[OLAPIException](../OLAPIException.md)

      [`getLocalizedMessage`](../OLAPIException.md)`, `[`getLocalizedMessage`](../OLAPIException.md)`, `[`toString`](../OLAPIException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NotCommittableException

          public NotCommittableException(java.lang.String message)

      Creates a `NotCommittableException` with the specified message.
      Parameters:
      `message` - A `String` that contains a message for the exception.

    <!-- -->

    - #### NotCommittableException

          public NotCommittableException(java.lang.String message,
                                         java.lang.String param)

      Creates a `NotCommittableException` with the specified message.
      Parameters:
      `message` - A `String` that contains a message for the exception.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](IncrementalChangeException.md)
- [Next Class](NotPreparedException.md)

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
