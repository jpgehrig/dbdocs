Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](OLAPIException.md)
- [Next Class](OLAPIRuntimeException.md)

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

oracle.olapi

## Class OLAPIIllegalStateException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - java.lang.IllegalStateException

        - - oracle.olapi.OLAPIIllegalStateException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](HasLocalizedMessage.md)

  <!-- -->

  Direct Known Subclasses:
  [ActiveSubtransactionsException](transaction/ActiveSubtransactionsException.md), [ObjectClosedException](../express/ObjectClosedException.md), [TransactionInactiveException](transaction/TransactionInactiveException.md)

  ------------------------------------------------------------------------



      public abstract class OLAPIIllegalStateException
      extends java.lang.IllegalStateException
      implements HasLocalizedMessage

  A common superclass for all exceptions that indicate that an operation cannot succeed because the state of the `DataProvider` or `Transaction` does not support it.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                         |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getLocalizedMessage``()`<br>Gets a message in the language specified by the default `java.util.Locale`.                       |
    | `java.lang.String` | `getLocalizedMessage``(java.util.Locale locale)`<br>Gets a message in the language specified by the `java.util.Locale` object. |
    | `java.lang.String` | `toString``()`<br>Gets the message for this `OLAPIIllegalStateException`.                                                      |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getLocalizedMessage

          public java.lang.String getLocalizedMessage(java.util.Locale locale)

      Gets a message in the language specified by the `java.util.Locale` object.
      Specified by:
      [`getLocalizedMessage`](HasLocalizedMessage.md) in interface [`HasLocalizedMessage`](HasLocalizedMessage.md)

      Parameters:
      `locale` - The `Locale` object that specifies the language for the message.

      Returns:
      A `String` that has the message in the specified language.

    <!-- -->

    - #### getLocalizedMessage

          public java.lang.String getLocalizedMessage()

      Gets a message in the language specified by the default `java.util.Locale`.
      Overrides:
      `getLocalizedMessage` in class `java.lang.Throwable`

      Returns:
      A `String` that has the message in the language of the default `Locale`.

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Gets the message for this `OLAPIIllegalStateException`.
      Overrides:
      `toString` in class `java.lang.Throwable`

      Returns:
      A `String` that has the message for this `OLAPIIllegalStateException`.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](OLAPIException.md)
- [Next Class](OLAPIRuntimeException.md)

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
