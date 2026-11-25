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

- [Prev Class](ErrorDescription.md)
- [Next Class](ExpressServerException.md)

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

## Class ErrorStack

- java.lang.Object

- - oracle.express.ErrorStack

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../olapi/HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public final class ErrorStack
      extends java.lang.Object
      implements HasLocalizedMessage, java.io.Serializable

  An object that provides information about an exception that is related to Oracle OLAP execution. Such an exception can be associated with several related errors, and each error is represented in the `ErrorStack`. The `getErrorDescriptions` method returns an `ErrorDescription` for each error on the stack.
  In general, the descriptive information that is provided by an `ErrorDescription` is useful only to Oracle staff who are debugging an internal problem. Typically, it is not meaningful to application developers.

  See Also:
  [`ErrorDescription`](ErrorDescription.md), [`ExpressServerException.getErrorStack()`](ExpressServerException.md), [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                                              |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `ERROR_CLASS_CORBA_SYSTEM`<br>A constant that indicates that the error was in the underlying connection components.                                                |
    | `static int`      | `ERROR_CLASS_EXPRESS_FAILURE`<br>A constant that indicates that the error was an Oracle OLAP error.                                                                |
    | `static int`      | `ERROR_CLASS_EXPRESS_FATAL`<br>A constant that indicates that the error was a fatal error in Oracle OLAP execution.                                                |
    | `static int`      | `ERROR_CLASS_EXPRESS_TERMINATE`<br>A constant that indicates that the error was such that the application can do nothing more and that it might as well terminate. |
    | `static int`      | `ERROR_CLASS_OLAPI`<br>A constant that indicates that the error was in the Oracle OLAP code.                                                                       |
    | `static int`      | `ERROR_CLASS_UNKNOWN_ERROR`<br>A constant that indicates that the error had an unknown cause.                                                                      |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                            |
    |--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`              | `getErrorClass``()`<br>Gets the class of error that applies to the first error that was encountered in this `ErrorStack`.                                                                         |
    | `java.util.List`   | `getErrorDescriptions``()`<br>Gets a list of `ErrorDescription` objects, each of which provides information about one error that occurred as part of the exception that has this `ErrorStack`.    |
    | `java.lang.String` | `getLocalizedMessage``()`<br>Gets a text representation of this `ErrorStack`, in the default `Locale` which includes short descriptions for all the errors in the stack.                          |
    | `java.lang.String` | `getLocalizedMessage``(java.util.Locale locale)`<br>Gets a text representation of this `ErrorStack`, in the specified `Locale` which includes short descriptions for all the errors in the stack. |
    | `java.lang.String` | `toString``()`<br>Gets a text representation of this `ErrorStack`, in the default `Locale` which includes short descriptions for all the errors in the stack.                                     |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### ERROR_CLASS_OLAPI

          public static final int ERROR_CLASS_OLAPI

      A constant that indicates that the error was in the Oracle OLAP code.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ERROR_CLASS_CORBA_SYSTEM

          public static final int ERROR_CLASS_CORBA_SYSTEM

      A constant that indicates that the error was in the underlying connection components.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ERROR_CLASS_UNKNOWN_ERROR

          public static final int ERROR_CLASS_UNKNOWN_ERROR

      A constant that indicates that the error had an unknown cause.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ERROR_CLASS_EXPRESS_FAILURE

          public static final int ERROR_CLASS_EXPRESS_FAILURE

      A constant that indicates that the error was an Oracle OLAP error.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ERROR_CLASS_EXPRESS_FATAL

          public static final int ERROR_CLASS_EXPRESS_FATAL

      A constant that indicates that the error was a fatal error in Oracle OLAP execution.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ERROR_CLASS_EXPRESS_TERMINATE

          public static final int ERROR_CLASS_EXPRESS_TERMINATE

      A constant that indicates that the error was such that the application can do nothing more and that it might as well terminate.
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getErrorDescriptions

          public final java.util.List getErrorDescriptions()

      Gets a list of `ErrorDescription` objects, each of which provides information about one error that occurred as part of the exception that has this `ErrorStack`. A given exception, such as an `ExpressServerException`, might have several `ErrorDescription` objects in its `ErrorStack`, one for the original error and one for each error that was triggered subsequently.
      Returns:
      A `List` that contains one `ErrorDescription` for each error that occurred as part of the exception that has this `ErrorStack`.

    <!-- -->

    - #### getErrorClass

          public final int getErrorClass()

      Gets the class of error that applies to the first error that was encountered in this `ErrorStack`.
      Returns:
      A constant that indicates the class of error that applies to the first error that was encountered in this `ErrorStack`. The constant must be one of the `ERROR_CLASS` fields in this class.

    <!-- -->

    - #### getLocalizedMessage

          public java.lang.String getLocalizedMessage(java.util.Locale locale)

      Gets a text representation of this `ErrorStack`, in the specified `Locale` which includes short descriptions for all the errors in the stack.
      Specified by:
      [`getLocalizedMessage`](../olapi/HasLocalizedMessage.md) in interface [`HasLocalizedMessage`](../olapi/HasLocalizedMessage.md)

      Parameters:
      `locale` - The `Locale` to use for translating the message.

      Returns:
      The message translated for the specified `Locale`.

    <!-- -->

    - #### getLocalizedMessage

          public java.lang.String getLocalizedMessage()

      Gets a text representation of this `ErrorStack`, in the default `Locale` which includes short descriptions for all the errors in the stack.
      Returns:
      The message translated for the specified `Locale`.

    <!-- -->

    - #### toString

          public final java.lang.String toString()

      Gets a text representation of this `ErrorStack`, in the default `Locale` which includes short descriptions for all the errors in the stack.
      Overrides:
      `toString` in class `java.lang.Object`

      Returns:
      The message translated for the specified `Locale`.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](ErrorDescription.md)
- [Next Class](ExpressServerException.md)

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
