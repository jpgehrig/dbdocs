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

- **[Prev Class](ResourceManager.md)**
- **[Next Class](XSLTransformerBeanInfo.md)**

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

**oracle.xml.async**

## **Class XSLTransformer**

- **java.lang.Object**

- - **oracle.xml.async.XSLTransformer**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable, java.lang.Runnable**

  ------------------------------------------------------------------------

  **
  **

      public class XSLTransformer
      extends java.lang.Object
      implements java.io.Serializable, java.lang.Runnable

  **Applies XSL transformation in a background thread.**
  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                      |
    |----------------------------------------------------------------------------------|
    | `XSLTransformer``()`<br>XSLTransformer constructor                               |
    | `XSLTransformer``(int id)`<br>XSLTransformer constructor accepting an identifier |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                              | Method and Description                                                                                                                                                                                 |
    |----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                         | `addXSLTransformerErrorListener``(`[`XSLTransformerErrorListener`](XSLTransformerErrorListener.md)` p0)`<br>Adds an XSLTransformer error event listener                                                |
    | `void`                                                         | `addXSLTransformerListener``(`[`XSLTransformerListener`](XSLTransformerListener.md)` p0)`<br>Adds a XSLTransformer listener                                                                            |
    | `void`                                                         | `escapeNonASCIICharacters``(boolean yes)`<br>Sets the escape flag used by the XSL processor                                                                                                            |
    | `int`                                                          | `getId``()`<br>Returns the unique XSLTransformer id                                                                                                                                                    |
    | [`DocumentFragment`](../../../org/w3c/dom/DocumentFragment.md) | `getResult``()`<br>Returns the document fragment for the resulting document.                                                                                                                           |
    | `void`                                                         | `processXSL``(`[`XSLStylesheet`](../parser/v2/XSLStylesheet.md)` xsl, java.io.InputStream xml, java.net.URL ref)`<br>Initiates XSL Transformation in the background.                                   |
    | `void`                                                         | `processXSL``(`[`XSLStylesheet`](../parser/v2/XSLStylesheet.md)` xsl, java.io.Reader xml, java.net.URL ref)`<br>Initiates XSL Transformation in the background.                                        |
    | `void`                                                         | `processXSL``(`[`XSLStylesheet`](../parser/v2/XSLStylesheet.md)` xsl, java.net.URL xml, java.net.URL ref)`<br>Initiates XSL Transformation in the background.                                          |
    | `void`                                                         | `processXSL``(`[`XSLStylesheet`](../parser/v2/XSLStylesheet.md)` xsl, `[`XMLDocument`](../parser/v2/XMLDocument.md)` xml)`<br>Initiates XSL Transformation in the background.                          |
    | `void`                                                         | `processXSL``(`[`XSLStylesheet`](../parser/v2/XSLStylesheet.md)` xsl, `[`XMLDocument`](../parser/v2/XMLDocument.md)` xml, java.io.OutputStream os)`<br>Initiates XSL Transformation in the background. |
    | `void`                                                         | `removeDOMTransformerErrorListener``(`[`XSLTransformerErrorListener`](XSLTransformerErrorListener.md)` p0)`<br>Removes an XSLTransformer error event listener                                          |
    | `void`                                                         | `removeXSLTransformerListener``(`[`XSLTransformerListener`](XSLTransformerListener.md)` p0)`<br>Removes a XSLTransformer listener                                                                      |
    | `void`                                                         | `run``()`<br>Starts a separate thread to do the XSL Transformation.                                                                                                                                    |
    | `void`                                                         | `setErrorStream``(java.io.OutputStream out)`<br>Sets the error stream used by the XSL processor                                                                                                        |
    | `void`                                                         | `setXSLTVersion``(`[`XSLProcessor.XSLTVersion`](../parser/v2/XSLProcessor.XSLTVersion.md)` ver)`<br>Sets the XSLT Version flag used by the XSL processor                                               |
    | `void`                                                         | `showWarnings``(boolean yes)`<br>Sets the showWarnings flag used by the XSL processor                                                                                                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSLTransformer

          public XSLTransformer()

      XSLTransformer constructor

    <!-- -->

    - #### XSLTransformer

          public XSLTransformer(int id)

      XSLTransformer constructor accepting an identifier
      Parameters:
      `id` - - A unique integer that can be used to identify the XSLTransformer instance during event processing

  <!-- -->

  - ### Method Detail

    - #### getId

          public int getId()

      Returns the unique XSLTransformer id
      Returns:
      The id of this XSLTransformer.

    <!-- -->

    - #### run

          public void run()

      Starts a separate thread to do the XSL Transformation.
      Specified by:
      `run` in interface `java.lang.Runnable`

    <!-- -->

    - #### addXSLTransformerListener

          public void addXSLTransformerListener(XSLTransformerListener p0)

      Adds a XSLTransformer listener
      Parameters:
      `p0` - XSLTransformerListener to be added

    <!-- -->

    - #### addXSLTransformerErrorListener

          public void addXSLTransformerErrorListener(XSLTransformerErrorListener p0)

      Adds an XSLTransformer error event listener
      Parameters:
      `p0` - XSLTransformerErrorListener to be added

    <!-- -->

    - #### removeXSLTransformerListener

          public void removeXSLTransformerListener(XSLTransformerListener p0)

      Removes a XSLTransformer listener
      Parameters:
      `p0` - XSLTransformerListener to be removed

    <!-- -->

    - #### removeDOMTransformerErrorListener

          public void removeDOMTransformerErrorListener(XSLTransformerErrorListener p0)

      Removes an XSLTransformer error event listener
      Parameters:
      `p0` - XSLTransformerErrorListener to be removed

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 XMLDocument xml)
                          throws XSLException

      Initiates XSL Transformation in the background. The control is returned immediately.
      Parameters:
      `xsl` - The stylesheet to be used for XSL transformation

      `xml` - The XML document to be used (as a DOM Tree)

      Throws:
      [`XSLException`](../parser/v2/XSLException.md) - if an error occurs during XSL transformation

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 java.io.InputStream xml,
                                 java.net.URL ref)
                          throws XSLException

      Initiates XSL Transformation in the background. The control is returned immediately.
      Parameters:
      `xsl` - The stylesheet to be used for XSL transformation

      `xml` - The XML document to be used (as a java.io.InputStream)

      `ref` - Reference URL to resolve external entities in input XML

      Throws:
      [`XSLException`](../parser/v2/XSLException.md) - if an error occurs during XSL transformation

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 java.io.Reader xml,
                                 java.net.URL ref)
                          throws XSLException

      Initiates XSL Transformation in the background. The control is returned immediately.
      Parameters:
      `xsl` - The stylesheet to be used for XSL transformation

      `xml` - The XML document to be used (as a java.io.Reader)

      `ref` - Reference URL to resolve external entities in input XML

      Throws:
      [`XSLException`](../parser/v2/XSLException.md) - if an error occurs during XSL transformation

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 java.net.URL xml,
                                 java.net.URL ref)
                          throws XSLException

      Initiates XSL Transformation in the background. The control is returned immediately.
      Parameters:
      `xsl` - The stylesheet to be used for XSL transformation

      `xml` - The XML document to be used (as a java.net.URL)

      `ref` - Reference URL to resolve external entities in input XML

      Throws:
      [`XSLException`](../parser/v2/XSLException.md) - if an error occurs during XSL transformation

    <!-- -->

    - #### processXSL

          public void processXSL(XSLStylesheet xsl,
                                 XMLDocument xml,
                                 java.io.OutputStream os)
                          throws XSLException

      Initiates XSL Transformation in the background. The control is returned immediately.
      Parameters:
      `xsl` - The stylesheet to be used for XSL transformation

      `xml` - The XML document to be used (as a DOM Tree)

      `os` - Outputstream to which the XSL transformation result is written

      Throws:
      [`XSLException`](../parser/v2/XSLException.md) - if an error occurs during XSL transformation

    <!-- -->

    - #### setErrorStream

          public final void setErrorStream(java.io.OutputStream out)
                                    throws java.io.IOException

      Sets the error stream used by the XSL processor
      Parameters:
      `out` - The error output stream for the XSL processor

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### showWarnings

          public final void showWarnings(boolean yes)

      Sets the showWarnings flag used by the XSL processor
      Parameters:
      `yes` - Boolean indicating if XSL processor warnings to be shown or not.

    <!-- -->

    - #### escapeNonASCIICharacters

          public final void escapeNonASCIICharacters(boolean yes)

      Sets the escape flag used by the XSL processor
      Parameters:
      `yes` - Boolean indicating if XSL processor should escape Non ASCII characters.

    <!-- -->

    - #### setXSLTVersion

          public final void setXSLTVersion(XSLProcessor.XSLTVersion ver)

      Sets the XSLT Version flag used by the XSL processor
      Parameters:
      `ver` - XSLTVersion.XSLT10 or XSLTVersion.XSLT20

    <!-- -->

    - #### getResult

          public DocumentFragment getResult()

      Returns the document fragment for the resulting document. Call this method only after receiving notification that the transformation is complete. Since the transformation occurs in background and asyncronously, calling this method immediately after processXSL will result in holding the control until the result is avialable.
      Returns:
      The resulting document fragment of the XSL transformation.

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

- **[Prev Class](ResourceManager.md)**
- **[Next Class](XSLTransformerBeanInfo.md)**

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
