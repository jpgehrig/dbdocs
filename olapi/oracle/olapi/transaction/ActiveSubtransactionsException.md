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

- Prev Class
- [Next Class](CommitException.md)

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

## Class ActiveSubtransactionsException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - java.lang.IllegalStateException

        - - [oracle.olapi.OLAPIIllegalStateException](../OLAPIIllegalStateException.md)

          - - oracle.olapi.transaction.ActiveSubtransactionsException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class ActiveSubtransactionsException
      extends OLAPIIllegalStateException

  Indicates that the current `Transaction` has child `Transaction` objects that the application must commit or roll back before committing or rolling back the current `Transaction`.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                     |
    |-----------------------------------------------------------------------------------------------------------------|
    | `ActiveSubtransactionsException``(java.util.List transactions)`<br>Creates an `ActiveSubtransactionsException`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                        |
    |-------------------|---------------------------------------------------------------------------------------------------------------|
    | `java.util.List`  | `getActiveSubTransactions``()`<br>Gets a `List` of the active child `Transaction` objects of a `Transaction`. |

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

    - #### ActiveSubtransactionsException

          public ActiveSubtransactionsException(java.util.List transactions)

      Creates an `ActiveSubtransactionsException`.
      Parameters:
      `transactions` - A `List` of the `Transaction` objects that are active children of a `Transaction`.

  <!-- -->

  - ### Method Detail

    - #### getActiveSubTransactions

          public java.util.List getActiveSubTransactions()

      Gets a `List` of the active child `Transaction` objects of a `Transaction`. A child `Transaction` is active until it is either committed or it is rolled back.
      Returns:
      A `List` of the active child `Transaction` objects of a `Transaction`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- Prev Class
- [Next Class](CommitException.md)

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
