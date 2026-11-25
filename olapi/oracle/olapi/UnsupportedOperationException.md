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

- [Prev Class](OLAPIRuntimeException.md)
- Next Class

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

## Class UnsupportedOperationException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - [oracle.olapi.OLAPIRuntimeException](OLAPIRuntimeException.md)

        - - oracle.olapi.UnsupportedOperationException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class UnsupportedOperationException
      extends OLAPIRuntimeException

  Indicates that Oracle OLAP does not support the operation requested by the application.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                           |
    |---------------------------------------------------------------------------------------------------------------------------------------|
    | `UnsupportedOperationException``()`<br>Creates an `UnsupportedOperationException`.                                                    |
    | `UnsupportedOperationException``(java.lang.String message)`<br>Creates an `UnsupportedOperationException` with the specified message. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.olapi.[OLAPIRuntimeException](OLAPIRuntimeException.md)

      [`getLocalizedMessage`](OLAPIRuntimeException.md)`, `[`getLocalizedMessage`](OLAPIRuntimeException.md)`, `[`getParameters`](OLAPIRuntimeException.md)`, `[`toString`](OLAPIRuntimeException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### UnsupportedOperationException

          public UnsupportedOperationException()

      Creates an `UnsupportedOperationException`.

    <!-- -->

    - #### UnsupportedOperationException

          public UnsupportedOperationException(java.lang.String message)

      Creates an `UnsupportedOperationException` with the specified message.
      Parameters:
      `message` - The message to associate with the exception.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](OLAPIRuntimeException.md)
- Next Class

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
