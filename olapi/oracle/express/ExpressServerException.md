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

- [Prev Class](ErrorStack.md)
- [Next Class](ObjectClosedException.md)

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

oracle.express

## Class ExpressServerException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - [oracle.olapi.OLAPIRuntimeException](../olapi/OLAPIRuntimeException.md)

        - - oracle.express.ExpressServerException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../olapi/HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public final class ExpressServerException
      extends OLAPIRuntimeException

  Indicates that the internal Oracle OLAP code cannot fulfill a request that was made by the OLAP API client code. The `getErrorStack` method makes it possible to investigate the source of the error more exactly; however, such investigation is only relevant to Oracle staff who are debugging an internal problem. Typically, it is not meaningful to application developers.
  See Also:
  [`ErrorDescription`](ErrorDescription.md), [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type             | Method and Description                                                                                                                            |
    |-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ErrorStack`](ErrorStack.md) | `getErrorStack``()`<br>Gets the `ErrorStack` for this `ExpressServerException`.                                                                   |
    | `java.lang.String`            | `toString``()`<br>Gets a text representation of this `ExpressServerException`, which includes short descriptions of all the errors that occurred. |

    - ### Methods inherited from class oracle.olapi.[OLAPIRuntimeException](../olapi/OLAPIRuntimeException.md)

      [`getLocalizedMessage`](../olapi/OLAPIRuntimeException.md)`, `[`getLocalizedMessage`](../olapi/OLAPIRuntimeException.md)`, `[`getParameters`](../olapi/OLAPIRuntimeException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getErrorStack

          public final ErrorStack getErrorStack()

      Gets the `ErrorStack` for this `ExpressServerException`. A given `ExpressServerException` can have several `ErrorDescription` objects, one for the original error and one for each error that was triggered subsequently. The `ErrorStack` for an exception records all of the related errors. Use the `getDescriptions` method on the `ErrorStack` to obtain a `List` of the `ErrorDescription` objects.
      Returns:
      The `ErrorStack` for this `ExpressServerException`.

    <!-- -->

    - #### toString

          public final java.lang.String toString()

      Gets a text representation of this `ExpressServerException`, which includes short descriptions of all the errors that occurred.
      Overrides:
      [`toString`](../olapi/OLAPIRuntimeException.md) in class [`OLAPIRuntimeException`](../olapi/OLAPIRuntimeException.md)

      Returns:
      A `String` that contains a text representation of this `ExpressServerException`, which includes short descriptions of all the errors that occurred.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](ErrorStack.md)
- [Next Class](ObjectClosedException.md)

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
