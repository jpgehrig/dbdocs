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

- [Prev Class](NotCommittableException.md)
- [Next Class](Transaction.md)

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

## Class NotPreparedException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - [oracle.olapi.OLAPIRuntimeException](../OLAPIRuntimeException.md)

        - - oracle.olapi.transaction.NotPreparedException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class NotPreparedException
      extends OLAPIRuntimeException

  Indicates that the `TransactionProvider` has not prepared the current `Transaction` and therefore it cannot commit the `Transaction`.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                  |
    |--------------------------------------------------------------------------------------------------------------|
    | `NotPreparedException``(`[`Transaction`](Transaction.md)` transaction)`<br>Creates a `NotPreparedException`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type               | Method and Description                                                     |
    |---------------------------------|----------------------------------------------------------------------------|
    | [`Transaction`](Transaction.md) | `getTransaction``()`<br>Gets the `Transaction` that has not been prepared. |

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

    - #### NotPreparedException

          public NotPreparedException(Transaction transaction)

      Creates a `NotPreparedException`.
      Parameters:
      `transaction` - The `Transaction` that has not been prepared.

  <!-- -->

  - ### Method Detail

    - #### getTransaction

          public Transaction getTransaction()

      Gets the `Transaction` that has not been prepared.
      Returns:
      The `Transaction` that has not been prepared.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](NotCommittableException.md)
- [Next Class](Transaction.md)

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
