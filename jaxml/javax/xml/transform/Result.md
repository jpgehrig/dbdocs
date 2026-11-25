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

- **[Prev Class](OutputKeys.md)**
- **[Next Class](Source.md)**

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

**javax.xml.transform**

## **Interface Result**

- **All Known Implementing Classes:**
  **[DOMResult](dom/DOMResult.md), [SAXResult](sax/SAXResult.md), [StreamResult](stream/StreamResult.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Result

  **An object that implements this interface contains the information needed to build a transformation result tree.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                                                                                  |
    |---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `PI_DISABLE_OUTPUT_ESCAPING`<br>The name of the processing instruction that is sent if the result tree disables output escaping.                                                                                       |
    | `static java.lang.String` | `PI_ENABLE_OUTPUT_ESCAPING`<br>The name of the processing instruction that is sent if the result tree enables output escaping at some point after having received a PI_DISABLE_OUTPUT_ESCAPING processing instruction. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                   |
    |--------------------|------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getSystemId``()`<br>Get the system identifier that was set with setSystemId.            |
    | `void`             | `setSystemId``(java.lang.String systemId)`<br>Set the system identifier for this Result. |

<!-- -->

- - ### Field Detail

    - #### PI_DISABLE_OUTPUT_ESCAPING

          static final java.lang.String PI_DISABLE_OUTPUT_ESCAPING

      The name of the processing instruction that is sent if the result tree disables output escaping.
      Normally, result tree serialization escapes & and \< (and possibly other characters) when outputting text nodes. This ensures that the output is well-formed XML. However, it is sometimes convenient to be able to produce output that is almost, but not quite well-formed XML; for example, the output may include ill-formed sections that will be transformed into well-formed XML by a subsequent non-XML aware process. If a processing instruction is sent with this name, serialization should be output without any escaping.

      Result DOM trees may also have PI_DISABLE_OUTPUT_ESCAPING and PI_ENABLE_OUTPUT_ESCAPING inserted into the tree.

      See Also:
      [disable-output-escaping in XSLT Specification](http://www.w3.org/TR/xslt#disable_output_escaping), [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PI_ENABLE_OUTPUT_ESCAPING

          static final java.lang.String PI_ENABLE_OUTPUT_ESCAPING

      The name of the processing instruction that is sent if the result tree enables output escaping at some point after having received a PI_DISABLE_OUTPUT_ESCAPING processing instruction.
      See Also:
      [disable-output-escaping in XSLT Specification](http://www.w3.org/TR/xslt#disable_output_escaping), [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### setSystemId

          void setSystemId(java.lang.String systemId)

      Set the system identifier for this Result.
      If the Result is not to be written to a file, the system identifier is optional. The application may still want to provide one, however, for use in error messages and warnings, or to resolve relative output identifiers.

      Parameters:
      `systemId` - The system identifier as a URI string.

    <!-- -->

    - #### getSystemId

          java.lang.String getSystemId()

      Get the system identifier that was set with setSystemId.
      Returns:
      The system identifier that was set with setSystemId, or null if setSystemId was not called.

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

- **[Prev Class](OutputKeys.md)**
- **[Next Class](Source.md)**

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
