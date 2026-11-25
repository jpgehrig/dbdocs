Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](BuildResult.md)
- [Next Class](CompoundCursorInfoSpecification.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.olapi.data.source

## Class BuildWarningsException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - [oracle.olapi.OLAPIRuntimeException](../../OLAPIRuntimeException.md)

        - - oracle.olapi.data.source.BuildWarningsException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../../HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public final class BuildWarningsException
      extends OLAPIRuntimeException

  Indicates that the attempt to build succeeded, but that there are warning messages.
  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                 |
    |-----------------------|--------------------------------------------------------------------------------------------------------|
    | `java.lang.Exception` | `getBaseException``()`<br>Gets an `Exception` that contains information about the error that occurred. |
    | `java.lang.String`    | `getErrorText``()`<br>Gets a `String` that contains information about the error that occurred.         |

    - ### Methods inherited from class oracle.olapi.[OLAPIRuntimeException](../../OLAPIRuntimeException.md)

      [`getLocalizedMessage`](../../OLAPIRuntimeException.md)`, `[`getLocalizedMessage`](../../OLAPIRuntimeException.md)`, `[`getParameters`](../../OLAPIRuntimeException.md)`, `[`toString`](../../OLAPIRuntimeException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getErrorText

          public java.lang.String getErrorText()

      Gets a `String` that contains information about the error that occurred.
      Returns:
      A `String` that contains information about the error condition.

    <!-- -->

    - #### getBaseException

          public java.lang.Exception getBaseException()

      Gets an `Exception` that contains information about the error that occurred.
      Returns:
      An `Exception` that contains information about the error condition.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](BuildResult.md)
- [Next Class](CompoundCursorInfoSpecification.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
