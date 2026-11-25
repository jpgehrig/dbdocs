Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XMLError.md)**
- **[Next Class](XMLMultiHandler.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**oracle.xml.parser.v2**

## **Interface XMLLocator**

- **All Superinterfaces:**
  **[Locator](../../../../org/xml/sax/Locator.md), [Locator2](../../../../org/xml/sax/ext/Locator2.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XMLLocator
      extends Locator2

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                              |
    |--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getDeclEncoding``()`<br>Returns the name of the character encoding declared This may be different from the actuall enconding used which is retruned by getEncoding |
    | `java.lang.String` | `getStandalone``()`<br>Get the standalone attribute in XML Declaration                                                                                              |

    - ### Methods inherited from interface org.xml.sax.ext.[Locator2](../../../../org/xml/sax/ext/Locator2.md)

      [`getEncoding`](../../../../org/xml/sax/ext/Locator2.md)`, `[`getXMLVersion`](../../../../org/xml/sax/ext/Locator2.md)

    <!-- -->

    - ### Methods inherited from interface org.xml.sax.[Locator](../../../../org/xml/sax/Locator.md)

      [`getColumnNumber`](../../../../org/xml/sax/Locator.md)`, `[`getLineNumber`](../../../../org/xml/sax/Locator.md)`, `[`getPublicId`](../../../../org/xml/sax/Locator.md)`, `[`getSystemId`](../../../../org/xml/sax/Locator.md)

<!-- -->

- - ### Method Detail

    - #### getStandalone

          java.lang.String getStandalone()

      Get the standalone attribute in XML Declaration
      Returns:
      String value of the standalone attribute either "yes" or "no"

    <!-- -->

    - #### getDeclEncoding

          java.lang.String getDeclEncoding()

      Returns the name of the character encoding declared This may be different from the actuall enconding used which is retruned by getEncoding

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XMLError.md)**
- **[Next Class](XMLMultiHandler.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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
