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

- **[Prev Class](Result.md)**
- **[Next Class](SourceLocator.md)**

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

## **Interface Source**

- **All Known Implementing Classes:**
  **[DOMSource](dom/DOMSource.md), [SAXSource](sax/SAXSource.md), [StreamSource](stream/StreamSource.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Source

  **An object that implements this interface contains the information needed to act as source input (XML source or transformation instructions).**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                   |
    |--------------------|------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getSystemId``()`<br>Get the system identifier that was set with setSystemId.            |
    | `void`             | `setSystemId``(java.lang.String systemId)`<br>Set the system identifier for this Source. |

<!-- -->

- - ### Method Detail

    - #### setSystemId

          void setSystemId(java.lang.String systemId)

      Set the system identifier for this Source.
      The system identifier is optional if the source does not get its data from a URL, but it may still be useful to provide one. The application can use a system identifier, for example, to resolve relative URIs and to include in error messages and warnings.

      Parameters:
      `systemId` - The system identifier as a URL string.

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

- **[Prev Class](Result.md)**
- **[Next Class](SourceLocator.md)**

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
