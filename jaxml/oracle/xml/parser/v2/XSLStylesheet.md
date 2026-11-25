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

- **[Prev Class](XSLProcessor.XSLTVersion.md)**
- **[Next Class](XSLTContext.md)**

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

## **Class XSLStylesheet**

- **java.lang.Object**

- - **oracle.xml.parser.v2.XSLStylesheet**

<!-- -->

- **All Implemented Interfaces:**
  **[Templates](../../../../javax/xml/transform/Templates.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XSLStylesheet
      extends java.lang.Object
      implements Templates

  **The class holds XSL stylesheet information such as templates, keys, variables, and attribute sets. The same stylesheet, once constructed, can be used to transform multiple XML documents.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                             |
    |-----------------------------------------------------------------------------------------------------------------------------------------|
    | `XSLStylesheet``()`<br>Deprecated. <br>Use XSLProcessor.newXSLStylesheet instead                                                        |
    | `XSLStylesheet``(java.io.InputStream xsl, java.net.URL ref)`<br>Deprecated. <br>Use XSLProcessor.newXSLStylesheet instead               |
    | `XSLStylesheet``(java.io.Reader xsl, java.net.URL ref)`<br>Deprecated. <br>Use XSLProcessor.newXSLStylesheet instead                    |
    | `XSLStylesheet``(java.net.URL xsl, java.net.URL ref)`<br>Deprecated. <br>Use XSLProcessor.newXSLStylesheet instead                      |
    | `XSLStylesheet``(`[`XMLDocument`](XMLDocument.md)` xsl, java.net.URL ref)`<br>Deprecated. <br>Use XSLProcessor.newXSLStylesheet instead |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                               | Method and Description                                                                                                            |
    |-----------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                          | `error``(java.lang.String msg, int errId)`<br>Deprecated.                                                                         |
    | `void`                                                          | `execute``(`[`XSLTContext`](XSLTContext.md)` context)`<br>Deprecated. <br>should use XSLProcessor.processXSL function             |
    | `java.lang.String`                                              | `getOutputEncoding``()`<br>Get the value of the encoding specified in `xsl:output`                                                |
    | `java.lang.String`                                              | `getOutputMediaType``()`<br>Get the value of the media-type specified in `xsl:output`                                             |
    | `java.util.Properties`                                          | `getOutputProperties``()`<br>Gets the output properties of the stylesheet                                                         |
    | [`Transformer`](../../../../javax/xml/transform/Transformer.md) | `newTransformer``()`<br>Create a new Transformer for XSL Transformation                                                           |
    | `void`                                                          | `removeParam``(java.lang.String name)`<br>Deprecated. <br>use XSLProcessor.removeParam to ensure thread safety                    |
    | `void`                                                          | `resetParams``()`<br>Deprecated. <br>use XSLProcessor.resetParams to ensure thread safety                                         |
    | `void`                                                          | `setParam``(java.lang.String name, java.lang.String value)`<br>Deprecated. <br>use XSLProcessor.setParams to ensure thread safety |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSLStylesheet

          public XSLStylesheet()
                        throws XSLException

      Deprecated. Use XSLProcessor.newXSLStylesheet instead
      Constructs an empty XSLStylesheet
      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### XSLStylesheet

          public XSLStylesheet(XMLDocument xsl,
                               java.net.URL ref)
                        throws XSLException

      Deprecated. Use XSLProcessor.newXSLStylesheet instead
      Constructs an XSLStylesheet using the given XMLDocument
      Parameters:
      `xsl` - XSL input as a DOM Tree

      `ref` - Reference URL for include, import

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### XSLStylesheet

          public XSLStylesheet(java.io.InputStream xsl,
                               java.net.URL ref)
                        throws XSLException

      Deprecated. Use XSLProcessor.newXSLStylesheet instead
      Constructs an XSLStylesheet using the given Inputstream
      Parameters:
      `xsl` - XSL input as an Inputstream

      `ref` - Reference URL for include, import and external entities

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### XSLStylesheet

          public XSLStylesheet(java.net.URL xsl,
                               java.net.URL ref)
                        throws XSLException

      Deprecated. Use XSLProcessor.newXSLStylesheet instead
      Constructs an XSLStylesheet using the given URL
      Parameters:
      `xsl` - XSL input as a URL

      `ref` - Reference URL for include, import and external entities

      Throws:
      [`XSLException`](XSLException.md) - on error.

    <!-- -->

    - #### XSLStylesheet

          public XSLStylesheet(java.io.Reader xsl,
                               java.net.URL ref)
                        throws XSLException

      Deprecated. Use XSLProcessor.newXSLStylesheet instead
      Constructs an XSLStylesheet using the given Reader
      Parameters:
      `xsl` - XSL input as a Reader

      `ref` - Reference URL for include, import and external entities

      Throws:
      [`XSLException`](XSLException.md) - on error.

  <!-- -->

  - ### Method Detail

    - #### getOutputMediaType

          public java.lang.String getOutputMediaType()

      Get the value of the media-type specified in `xsl:output`
      Returns:
      the media-type

    <!-- -->

    - #### getOutputEncoding

          public java.lang.String getOutputEncoding()

      Get the value of the encoding specified in `xsl:output`
      Returns:
      the encoding

    <!-- -->

    - #### removeParam

          public void removeParam(java.lang.String name)
                           throws XSLException

      Deprecated. use XSLProcessor.removeParam to ensure thread safety
      Removes the value of a top-level stylesheet parameter.
      Parameters:
      `name` - parameter name

      Throws:
      [`XSLException`](XSLException.md) - on error

    <!-- -->

    - #### resetParams

          public void resetParams()
                           throws XSLException

      Deprecated. use XSLProcessor.resetParams to ensure thread safety
      Resets all the params set.
      Throws:
      [`XSLException`](XSLException.md) - on error

    <!-- -->

    - #### setParam

          public void setParam(java.lang.String name,
                               java.lang.String value)
                        throws XSLException

      Deprecated. use XSLProcessor.setParams to ensure thread safety
      Sets the value of a top-level stylesheet parameter. The parameter value is expected to be a valid XPath expression (note that string literal values would therefore have to be explicitly quoted).
      Parameters:
      `name` - parameter name

      `value` - parameter value as an XPath expression

      Throws:
      [`XSLException`](XSLException.md) - on error

    <!-- -->

    - #### execute

          public void execute(XSLTContext context)
                       throws XSLException

      Deprecated. should use XSLProcessor.processXSL function
      Start the xsl processing.
      Parameters:
      `context` - XSLTContext used for XSL processing

      Throws:
      [`XSLException`](XSLException.md) - on error

    <!-- -->

    - #### error

          public void error(java.lang.String msg,
                            int errId)
                     throws XSLException

      Deprecated. 
      Throws:
      [`XSLException`](XSLException.md)

    <!-- -->

    - #### getOutputProperties

          public java.util.Properties getOutputProperties()

      Gets the output properties of the stylesheet
      Specified by:
      [`getOutputProperties`](../../../../javax/xml/transform/Templates.md) in interface [`Templates`](../../../../javax/xml/transform/Templates.md)

      Returns:
      the output properties

    <!-- -->

    - #### newTransformer

          public Transformer newTransformer()

      Create a new Transformer for XSL Transformation
      Specified by:
      [`newTransformer`](../../../../javax/xml/transform/Templates.md) in interface [`Templates`](../../../../javax/xml/transform/Templates.md)

      Returns:
      Transformer object

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

- **[Prev Class](XSLProcessor.XSLTVersion.md)**
- **[Next Class](XSLTContext.md)**

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
