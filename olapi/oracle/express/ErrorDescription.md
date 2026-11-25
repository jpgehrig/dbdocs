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

- Prev Class
- [Next Class](ErrorStack.md)

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

## Class ErrorDescription

- java.lang.Object

- - oracle.express.ErrorDescription

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../olapi/HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class ErrorDescription
      extends java.lang.Object
      implements HasLocalizedMessage, java.io.Serializable

  A description of an error that caused an OLAP API method to throw an exception that is related to execution in Oracle OLAP. Such an exception can be associated with several `ErrorDescription` objects, because the problem might have triggered several related errors. The `ErrorStack` associated with the exception records all of the related errors. To obtain all of the `ErrorDescription` objects for a particular Oracle OLAP related exception, call its `getErrorStack` method, and then call `getErrorDescriptions` on the `ErrorStack`.
  The description of a particular error is provided through the method calls on its `ErrorDescription`. For example, the `getErrorType` method returns one of two types of errors, and the `getDomain` method reports the area of Oracle OLAP functionality (called the domain) within which the error occurred.

  In general, the descriptive information that is provided by an `ErrorDescription` is useful only to Oracle staff who are debugging an internal problem. It is not meaningful to application developers.

  See Also:
  [`ErrorStack`](ErrorStack.md), [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                                |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `DOMAIN_CTL`<br>A constant indicating that an error occurred in the Oracle OLAP code for controllers, such as the controller for query execution.    |
    | `static int`      | `DOMAIN_CUR`<br>A constant indicating that an error occurred in the Oracle OLAP code for `Cursor` handling.                                          |
    | `static int`      | `DOMAIN_DEF`<br>A constant indicating that an error occurred in the Oracle OLAP code for `Source` definitions and query interpretation.              |
    | `static int`      | `DOMAIN_DPR`<br>A constant indicating that an error occurred in the Oracle OLAP code for providing data.                                             |
    | `static int`      | `DOMAIN_ECM`<br>A constant indicating that an error occurred in the Oracle OLAP code for supporting ECM.                                             |
    | `static int`      | `DOMAIN_ENG`<br>A constant indicating that an error occurred in the Oracle OLAP code in the engine.                                                  |
    | `static int`      | `DOMAIN_EXP`<br>A constant indicating that an error occurred in the Oracle OLAP code for expression generation.                                      |
    | `static int`      | `DOMAIN_INI`<br>A constant indicating that an error occurred in the Oracle OLAP code for connecting.                                                 |
    | `static int`      | `DOMAIN_INT`<br>A constant indicating that an error occurred in the Oracle OLAP code for internationalization.                                       |
    | `static int`      | `DOMAIN_MDP`<br>A constant indicating that an error occurred in the Oracle OLAP code for providing metadata.                                         |
    | `static int`      | `DOMAIN_OES`<br>A constant indicating that an error occurred in the Oracle OLAP code for supporting OLAP objects.                                    |
    | `static int`      | `DOMAIN_SCO`<br>A constant indicating that an error occurred in the Oracle OLAP code for SPL command objects.                                        |
    | `static int`      | `DOMAIN_SEL`<br>A constant indicating that an error occurred in the Oracle OLAP code for selection statements.                                       |
    | `static int`      | `DOMAIN_SPL`<br>A constant indicating that an error occurred in the Oracle OLAP code for the SPL.                                                    |
    | `static int`      | `DOMAIN_TRN`<br>A constant indicating that an error occurred in the Oracle OLAP code for transactions.                                               |
    | `static int`      | `ERROR_TYPE_GENERIC`<br>A constant indicating that a general error occurred, and that it did not involve a query with a valueless dimension or edge. |
    | `static int`      | `ERROR_TYPE_NULL_STATUS`<br>A constant indicating that an error occurred because a query resulted in a dimension or edge with no values.             |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                                                                               |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`              | `getDomain``()`<br>Gets the area of Oracle OLAP functionality (that is, the domain) in which the error occurred.                                                                                                                                                                     |
    | `int`              | `getErrorType``()`<br>Gets the type of the error.                                                                                                                                                                                                                                    |
    | `java.lang.String` | `getLocalizedMessage``()`<br>Gets a text representation of the `ErrorDescription` in the default `Locale` that includes the domain abbreviation, a short text description of the error, and an indication of where in the internal code the error occurred.                          |
    | `java.lang.String` | `getLocalizedMessage``(java.util.Locale locale)`<br>Gets a text representation of the `ErrorDescription` in the specified `Locale` that includes the domain abbreviation, a short text description of the error, and an indication of where in the internal code the error occurred. |
    | `java.lang.String` | `getMessage``()`<br>Gets a short text message describing the error.                                                                                                                                                                                                                  |
    | `java.lang.String` | `getSource``()`<br>Gets the class and method in which the error occurred within the internal Oracle OLAP code.                                                                                                                                                                       |
    | `java.lang.String` | `toString``()`<br>Gets a text representation of the `ErrorDescription` that includes the domain abbreviation, a short text description of the error, and an indication of where in the internal code the error occurred.                                                             |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### DOMAIN_ENG

          public static final int DOMAIN_ENG

      A constant indicating that an error occurred in the Oracle OLAP code in the engine.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOMAIN_MDP

          public static final int DOMAIN_MDP

      A constant indicating that an error occurred in the Oracle OLAP code for providing metadata.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOMAIN_OES

          public static final int DOMAIN_OES

      A constant indicating that an error occurred in the Oracle OLAP code for supporting OLAP objects.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOMAIN_ECM

          public static final int DOMAIN_ECM

      A constant indicating that an error occurred in the Oracle OLAP code for supporting ECM.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOMAIN_DPR

          public static final int DOMAIN_DPR

      A constant indicating that an error occurred in the Oracle OLAP code for providing data.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOMAIN_TRN

          public static final int DOMAIN_TRN

      A constant indicating that an error occurred in the Oracle OLAP code for transactions.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOMAIN_DEF

          public static final int DOMAIN_DEF

      A constant indicating that an error occurred in the Oracle OLAP code for `Source` definitions and query interpretation.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOMAIN_CUR

          public static final int DOMAIN_CUR

      A constant indicating that an error occurred in the Oracle OLAP code for `Cursor` handling.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOMAIN_SPL

          public static final int DOMAIN_SPL

      A constant indicating that an error occurred in the Oracle OLAP code for the SPL.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOMAIN_CTL

          public static final int DOMAIN_CTL

      A constant indicating that an error occurred in the Oracle OLAP code for controllers, such as the controller for query execution.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOMAIN_INI

          public static final int DOMAIN_INI

      A constant indicating that an error occurred in the Oracle OLAP code for connecting.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOMAIN_SCO

          public static final int DOMAIN_SCO

      A constant indicating that an error occurred in the Oracle OLAP code for SPL command objects.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOMAIN_INT

          public static final int DOMAIN_INT

      A constant indicating that an error occurred in the Oracle OLAP code for internationalization.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOMAIN_SEL

          public static final int DOMAIN_SEL

      A constant indicating that an error occurred in the Oracle OLAP code for selection statements.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOMAIN_EXP

          public static final int DOMAIN_EXP

      A constant indicating that an error occurred in the Oracle OLAP code for expression generation.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ERROR_TYPE_GENERIC

          public static final int ERROR_TYPE_GENERIC

      A constant indicating that a general error occurred, and that it did not involve a query with a valueless dimension or edge.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ERROR_TYPE_NULL_STATUS

          public static final int ERROR_TYPE_NULL_STATUS

      A constant indicating that an error occurred because a query resulted in a dimension or edge with no values.
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getMessage

          public final java.lang.String getMessage()

      Gets a short text message describing the error.
      Returns:
      A `String` that contains a short description of the error.

    <!-- -->

    - #### getSource

          public final java.lang.String getSource()

      Gets the class and method in which the error occurred within the internal Oracle OLAP code.
      Returns:
      A `String` that contains the names of the internal class and method in which the error occurred. The location of the class is within the Oracle OLAP code.

    <!-- -->

    - #### getDomain

          public final int getDomain()

      Gets the area of Oracle OLAP functionality (that is, the domain) in which the error occurred.
      Returns:
      A constant that indicates the area of Oracle OLAP functionality (that is, the domain) in which the error occurred. The constant must be one of the `DOMAIN` fields in this class.

    <!-- -->

    - #### getErrorType

          public final int getErrorType()

      Gets the type of the error.
      Returns:
      A constant that indicates the type of the error. The constant must be one of the `ERROR_TYPE` fields in this class.

    <!-- -->

    - #### getLocalizedMessage

          public java.lang.String getLocalizedMessage(java.util.Locale locale)

      Gets a text representation of the `ErrorDescription` in the specified `Locale` that includes the domain abbreviation, a short text description of the error, and an indication of where in the internal code the error occurred.
      Specified by:
      [`getLocalizedMessage`](../olapi/HasLocalizedMessage.md) in interface [`HasLocalizedMessage`](../olapi/HasLocalizedMessage.md)

      Parameters:
      `locale` - The `Locale` to use for translating the message.

      Returns:
      The message translated for the specified `Locale`.

    <!-- -->

    - #### getLocalizedMessage

          public java.lang.String getLocalizedMessage()

      Gets a text representation of the `ErrorDescription` in the default `Locale` that includes the domain abbreviation, a short text description of the error, and an indication of where in the internal code the error occurred.
      Returns:
      The message translated for the specified `Locale`.

    <!-- -->

    - #### toString

          public final java.lang.String toString()

      Gets a text representation of the `ErrorDescription` that includes the domain abbreviation, a short text description of the error, and an indication of where in the internal code the error occurred.
      Overrides:
      `toString` in class `java.lang.Object`

      Returns:
      A `String` that contains a text representation of the `ErrorDescription`. The text provides information about the error.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- Prev Class
- [Next Class](ErrorStack.md)

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
