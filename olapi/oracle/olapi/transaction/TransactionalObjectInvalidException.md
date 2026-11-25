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

- [Prev Class](Transaction.md)
- [Next Class](TransactionInactiveException.md)

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

## Class TransactionalObjectInvalidException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - [oracle.olapi.OLAPIRuntimeException](../OLAPIRuntimeException.md)

        - - oracle.olapi.transaction.TransactionalObjectInvalidException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class TransactionalObjectInvalidException
      extends OLAPIRuntimeException

  Indicates that the `TransactionalObject` is not valid in the current `Transaction`.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                   |
    |-----------------------------------------------------------------------------------------------|
    | `TransactionalObjectInvalidException``()`<br>Creates a `TransactionalObjectInvalidException`. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.olapi.[OLAPIRuntimeException](../OLAPIRuntimeException.md)

      [`getLocalizedMessage`](../OLAPIRuntimeException.md)`, `[`getLocalizedMessage`](../OLAPIRuntimeException.md)`, `[`getParameters`](../OLAPIRuntimeException.md)`, `[`toString`](../OLAPIRuntimeException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### TransactionalObjectInvalidException

          public TransactionalObjectInvalidException()

      Creates a `TransactionalObjectInvalidException`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](Transaction.md)
- [Next Class](TransactionInactiveException.md)

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
