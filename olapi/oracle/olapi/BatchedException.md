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

- [Prev Class](ArraySet.md)
- [Next Class](HasLocalizedMessage.md)

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

## Class BatchedException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - [oracle.olapi.OLAPIRuntimeException](OLAPIRuntimeException.md)

        - - oracle.olapi.BatchedException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class BatchedException
      extends OLAPIRuntimeException

  A base class for runtime exceptions that bundle together a list of errors or warnings for later processing.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                     | Method and Description                                                                                                         |
    |---------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
    | `java.util.List<java.lang.Exception>` | `getErrors``()`<br>Gets the exceptions of the `BatchedException` that are caused by errors.                                    |
    | `java.util.List<java.lang.Exception>` | `getExceptions``()`<br>Gets the exceptions that the `BatchedException` contains.                                               |
    | `java.lang.String`                    | `getLocalizedMessage``(java.util.Locale locale)`<br>Gets a message in the language specified by the `java.util.Locale` object. |
    | `java.util.List<java.lang.Exception>` | `getWarnings``()`<br>Gets the exceptions of the `BatchedException` that are warnings.                                          |
    | `boolean`                             | `isError``()`<br>Indicates that the exception is caused by an error.                                                           |
    | `boolean`                             | `isWarning``()`<br>Indicates that the exception is a warning about a potential problem.                                        |

    - ### Methods inherited from class oracle.olapi.[OLAPIRuntimeException](OLAPIRuntimeException.md)

      [`getLocalizedMessage`](OLAPIRuntimeException.md)`, `[`getParameters`](OLAPIRuntimeException.md)`, `[`toString`](OLAPIRuntimeException.md)

    <!-- -->

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

      Overrides:
      [`getLocalizedMessage`](OLAPIRuntimeException.md) in class [`OLAPIRuntimeException`](OLAPIRuntimeException.md)

      Parameters:
      `locale` - The `Locale` object that specifies the language for the message.

      Returns:
      A `String` that has the message in the specified language.

    <!-- -->

    - #### isWarning

          public final boolean isWarning()

      Indicates that the exception is a warning about a potential problem.
      Returns:
      A `boolean` that is `true` if the exception is a warning or `false` if not.

    <!-- -->

    - #### isError

          public final boolean isError()

      Indicates that the exception is caused by an error.
      Returns:
      A `boolean` that is `true` if the exception is caused by an error or `false` if not.

    <!-- -->

    - #### getExceptions

          public final java.util.List<java.lang.Exception> getExceptions()

      Gets the exceptions that the `BatchedException` contains.
      Returns:
      A `List` of `Exception` objects.

    <!-- -->

    - #### getErrors

          public final java.util.List<java.lang.Exception> getErrors()

      Gets the exceptions of the `BatchedException` that are caused by errors.
      Returns:
      A `List` of the `Exception` objects that are caused by errors.

    <!-- -->

    - #### getWarnings

          public final java.util.List<java.lang.Exception> getWarnings()

      Gets the exceptions of the `BatchedException` that are warnings.
      Returns:
      A `List` of the `Exception` objects that are warnings.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](ArraySet.md)
- [Next Class](HasLocalizedMessage.md)

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
