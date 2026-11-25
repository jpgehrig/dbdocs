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

- **[Prev Class](ValidationEventHandler.md)**
- **[Next Class](ValidationException.md)**

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

## **Interface ValidationEventLocator**

-

  ------------------------------------------------------------------------

  **
  **

      public interface ValidationEventLocator

  **Encapsulate the location of a ValidationEvent.**
  **The `ValidationEventLocator` indicates where the `ValidationEvent` occurred. Different fields will be set depending on the type of validation that was being performed when the error or warning was detected. For example, on-demand validation would produce locators that contained references to objects in the Java content tree while unmarshal-time validation would produce locators containing information appropriate to the source of the XML data (file, url, Node, etc).**

  **Since:**
  **JAXB1.0**

  **See Also:**
  **[`Validator`](Validator.md), [`ValidationEvent`](ValidationEvent.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                      | Method and Description                                                                    |
    |----------------------------------------|-------------------------------------------------------------------------------------------|
    | `int`                                  | `getColumnNumber``()`<br>Return the column number if available                            |
    | `int`                                  | `getLineNumber``()`<br>Return the line number if available                                |
    | [`Node`](../../../org/w3c/dom/Node.md) | `getNode``()`<br>Return a reference to the DOM Node if available                          |
    | `java.lang.Object`                     | `getObject``()`<br>Return a reference to the object in the Java content tree if available |
    | `int`                                  | `getOffset``()`<br>Return the byte offset if available                                    |
    | `java.net.URL`                         | `getURL``()`<br>Return the name of the XML source as a URL if available                   |

<!-- -->

- - ### Method Detail

    - #### getURL

          java.net.URL getURL()

      Return the name of the XML source as a URL if available
      Returns:
      the name of the XML source as a URL or null if unavailable

    <!-- -->

    - #### getOffset

          int getOffset()

      Return the byte offset if available
      Returns:
      the byte offset into the input source or -1 if unavailable

    <!-- -->

    - #### getLineNumber

          int getLineNumber()

      Return the line number if available
      Returns:
      the line number or -1 if unavailable

    <!-- -->

    - #### getColumnNumber

          int getColumnNumber()

      Return the column number if available
      Returns:
      the column number or -1 if unavailable

    <!-- -->

    - #### getObject

          java.lang.Object getObject()

      Return a reference to the object in the Java content tree if available
      Returns:
      a reference to the object in the Java content tree or null if unavailable

    <!-- -->

    - #### getNode

          Node getNode()

      Return a reference to the DOM Node if available
      Returns:
      a reference to the DOM Node or null if unavailable

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

- **[Prev Class](ValidationEventHandler.md)**
- **[Next Class](ValidationException.md)**

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
