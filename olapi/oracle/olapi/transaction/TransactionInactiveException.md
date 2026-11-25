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

- [Prev Class](TransactionalObjectInvalidException.md)
- [Next Class](TransactionProvider.md)

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

## Class TransactionInactiveException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - java.lang.IllegalStateException

        - - [oracle.olapi.OLAPIIllegalStateException](../OLAPIIllegalStateException.md)

          - - oracle.olapi.transaction.TransactionInactiveException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class TransactionInactiveException
      extends OLAPIIllegalStateException

  Indicates that the current `Transaction` has already been committed or rolled back by the application and is therefore no longer active.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                    |
    |--------------------------------------------------------------------------------------------------------------------------------|
    | `TransactionInactiveException``(`[`Transaction`](Transaction.md)` transaction)`<br>Creates a `TransactionTerminatedException`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type               | Method and Description                                   |
    |---------------------------------|----------------------------------------------------------|
    | [`Transaction`](Transaction.md) | `getTransaction``()`<br>Gets the inactive `Transaction`. |

    - ### Methods inherited from class oracle.olapi.[OLAPIIllegalStateException](../OLAPIIllegalStateException.md)

      [`getLocalizedMessage`](../OLAPIIllegalStateException.md)`, `[`getLocalizedMessage`](../OLAPIIllegalStateException.md)`, `[`toString`](../OLAPIIllegalStateException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### TransactionInactiveException

          public TransactionInactiveException(Transaction transaction)

      Creates a `TransactionTerminatedException`.
      Parameters:
      `transaction` - The `Transaction` that is inactive.

  <!-- -->

  - ### Method Detail

    - #### getTransaction

          public Transaction getTransaction()

      Gets the inactive `Transaction`.
      Returns:
      The `Transaction` that is inactive.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](TransactionalObjectInvalidException.md)
- [Next Class](TransactionProvider.md)

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
