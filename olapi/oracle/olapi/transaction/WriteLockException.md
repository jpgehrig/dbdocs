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

- [Prev Class](TransactionTypeUnavailableException.md)
- Next Class

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

## Class WriteLockException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - [oracle.olapi.OLAPIRuntimeException](../OLAPIRuntimeException.md)

        - - oracle.olapi.transaction.WriteLockException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class WriteLockException
      extends OLAPIRuntimeException

  Indicates that the `TransactionProvider` cannot create a write `Transaction` at this time. This exception occurs, for example, in an application that has a `Source` produced by a `Template`. The `Source` is active in a parent `Transaction` and the application has begun two child `Transaction` objects. If the application changes the state of the `Template` in one child `Transaction` and then attempts to change the state of the `Template` in the other child without having first prepared and committed the first child `Transaction` into the parent `Transaction`, then the `TransactionProvider` produces this exception.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                     |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `WriteLockException``(`[`MetadataState`](metadataStateManager/MetadataState.md)` state, `[`Transaction`](Transaction.md)` transaction, `[`Transaction`](Transaction.md)` activeTransaction)`<br>Creates a `WriteLockException`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                        | Method and Description                                                                                                                                                                                                                             |
    |----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Transaction`](Transaction.md)                          | `getActiveTransaction``()`<br>Gets the `Transaction` in which the `MetadataState` is currently being changed.                                                                                                                                      |
    | [`MetadataState`](metadataStateManager/MetadataState.md) | `getMetadataState``()`<br>Gets the `MetadataState` that cannot change state in the `Transaction` returned by the `getTransaction` method because the `MetadataState` is active in the `Transaction` returned by the `getActiveTransaction` method. |
    | [`Transaction`](Transaction.md)                          | `getTransaction``()`<br>Gets the `Transaction` in which the attempt to change a `MetadataState` failed because the `MetadataState` is not active in the `Transaction`.                                                                             |

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

    - #### WriteLockException

          public WriteLockException(MetadataState state,
                                    Transaction transaction,
                                    Transaction activeTransaction)

      Creates a `WriteLockException`.
      Parameters:
      `state` - The `MetadataState` that cannot change state.

      `transaction` - The `Transaction` in which the attempt to change the `MetadataState` failed.

      `activeTransaction` - The `Transaction` in which the `MetadataState` is active.

  <!-- -->

  - ### Method Detail

    - #### getMetadataState

          public MetadataState getMetadataState()

      Gets the `MetadataState` that cannot change state in the `Transaction` returned by the `getTransaction` method because the `MetadataState` is active in the `Transaction` returned by the `getActiveTransaction` method.
      Returns:
      The `MetadataState` that cannot change state.

    <!-- -->

    - #### getTransaction

          public Transaction getTransaction()

      Gets the `Transaction` in which the attempt to change a `MetadataState` failed because the `MetadataState` is not active in the `Transaction`.
      Returns:
      The `Transaction` in which the attempt to change the `MetadataState` failed.

    <!-- -->

    - #### getActiveTransaction

          public Transaction getActiveTransaction()

      Gets the `Transaction` in which the `MetadataState` is currently being changed. This `Transaction` must be prepared and committed, or rolled back, before another `Transaction` can change the `MetadataState`.
      Returns:
      The `Transaction` in which the `MetadataState` is active.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](TransactionTypeUnavailableException.md)
- Next Class

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
