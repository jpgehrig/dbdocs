Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](UnmarshallerHandler.md)**
- **[Next Class](ValidationEventHandler.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**javax.xml.bind**

## **Interface ValidationEvent**

- **All Known Subinterfaces:**
  **[NotIdentifiableEvent](NotIdentifiableEvent.md), [ParseConversionEvent](ParseConversionEvent.md), [PrintConversionEvent](PrintConversionEvent.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface ValidationEvent

  **This event indicates that a problem was encountered while validating the incoming XML data during an unmarshal operation or while performing on-demand validation of the Java content tree.**
  **Since:**
  **JAXB1.0**

  **See Also:**
  **[`Validator`](Validator.md), [`ValidationEventHandler`](ValidationEventHandler.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                                                           |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `ERROR`<br>Conditions that correspond to the definition of "error" in section 1.2 of the W3C XML 1.0 Recommendation             |
    | `static int`      | `FATAL_ERROR`<br>Conditions that correspond to the definition of "fatal error" in section 1.2 of the W3C XML 1.0 Recommendation |
    | `static int`      | `WARNING`<br>Conditions that are not errors or fatal errors as defined by the XML 1.0 recommendation                            |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                     | Method and Description                                                            |
    |-------------------------------------------------------|-----------------------------------------------------------------------------------|
    | `java.lang.Throwable`                                 | `getLinkedException``()`<br>Retrieve the linked exception for this warning/error. |
    | [`ValidationEventLocator`](ValidationEventLocator.md) | `getLocator``()`<br>Retrieve the locator for this warning/error.                  |
    | `java.lang.String`                                    | `getMessage``()`<br>Retrieve the text message for this warning/error.             |
    | `int`                                                 | `getSeverity``()`<br>Retrieve the severity code for this warning/error.           |

<!-- -->

- - ### Field Detail

    - #### WARNING

          static final int WARNING

      Conditions that are not errors or fatal errors as defined by the XML 1.0 recommendation
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ERROR

          static final int ERROR

      Conditions that correspond to the definition of "error" in section 1.2 of the W3C XML 1.0 Recommendation
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### FATAL_ERROR

          static final int FATAL_ERROR

      Conditions that correspond to the definition of "fatal error" in section 1.2 of the W3C XML 1.0 Recommendation
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getSeverity

          int getSeverity()

      Retrieve the severity code for this warning/error.
      Must be one of `ValidationError.WARNING`, `ValidationError.ERROR`, or `ValidationError.FATAL_ERROR`.

      Returns:
      the severity code for this warning/error

    <!-- -->

    - #### getMessage

          java.lang.String getMessage()

      Retrieve the text message for this warning/error.
      Returns:
      the text message for this warning/error or null if one wasn't set

    <!-- -->

    - #### getLinkedException

          java.lang.Throwable getLinkedException()

      Retrieve the linked exception for this warning/error.
      Returns:
      the linked exception for this warning/error or null if one wasn't set

    <!-- -->

    - #### getLocator

          ValidationEventLocator getLocator()

      Retrieve the locator for this warning/error.
      Returns:
      the locator that indicates where the warning/error occurred

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](UnmarshallerHandler.md)**
- **[Next Class](ValidationEventHandler.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
