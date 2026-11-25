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

- **[Prev Class](ErrorListener.md)**
- **[Next Class](Result.md)**

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

## **Class OutputKeys**

- **java.lang.Object**

- - **javax.xml.transform.OutputKeys**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class OutputKeys
      extends java.lang.Object

  **Provides string constants that can be used to set output properties for a Transformer, or to retrieve output properties from a Transformer or Templates object.**
  **A properties in this class are read-only.**

  **See Also:**
  **[section 16 of the XSL Transformations (XSLT) W3C Recommendation](http://www.w3.org/TR/xslt#output)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                  |
    |---------------------------|------------------------------------------------------------------------|
    | `static java.lang.String` | `CDATA_SECTION_ELEMENTS`<br>cdata-section-elements = `expanded names`. |
    | `static java.lang.String` | `DOCTYPE_PUBLIC`<br>doctype-public = `string`.                         |
    | `static java.lang.String` | `DOCTYPE_SYSTEM`<br>doctype-system = `string`.                         |
    | `static java.lang.String` | `ENCODING`<br>encoding = `string`.                                     |
    | `static java.lang.String` | `INDENT`<br>indent = "yes" \| "no".                                    |
    | `static java.lang.String` | `MEDIA_TYPE`<br>media-type = `string`.                                 |
    | `static java.lang.String` | `METHOD`<br>method = "xml" \| "html" \| "text" \| `expanded name`.     |
    | `static java.lang.String` | `OMIT_XML_DECLARATION`<br>omit-xml-declaration = "yes" \| "no".        |
    | `static java.lang.String` | `STANDALONE`<br>standalone = "yes" \| "no".                            |
    | `static java.lang.String` | `VERSION`<br>version = `nmtoken`.                                      |

  <!-- -->

  -

    ### **Method Summary**

    -

      ### **Methods inherited from class java.lang.Object**

      **`equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`**

<!-- -->

-
  -

    ### **Field Detail**

    - #### **METHOD**

          public static final java.lang.String METHOD

      **method = "xml" \| "html" \| "text" \| `expanded name`.**
      **The method attribute identifies the overall method that should be used for outputting the result tree. Other non-namespaced values may be used, such as "xhtml", but, if accepted, the handling of such values is implementation defined. If any of the method values are not accepted and are not namespace qualified, then [`Transformer.setOutputProperty(java.lang.String, java.lang.String)`](Transformer.md) or [`Transformer.setOutputProperties(java.util.Properties)`](Transformer.md) will throw a `IllegalArgumentException`.**

      **See Also:**
      **[section 16 of the XSL Transformations (XSLT) W3C Recommendation](http://www.w3.org/TR/xslt#output), [Constant Field Values](../../../constant-values.md)**

    - #### **VERSION**

          public static final java.lang.String VERSION

      **version = `nmtoken`.**
      **`version` specifies the version of the output method.**

      **When the output method is "xml", the version value specifies the version of XML to be used for outputting the result tree. The default value for the xml output method is 1.0. When the output method is "html", the version value indicates the version of the HTML. The default value for the xml output method is 4.0, which specifies that the result should be output as HTML conforming to the HTML 4.0 Recommendation \[HTML\]. If the output method is "text", the version property is ignored.**

      **See Also:**
      **[section 16 of the XSL Transformations (XSLT) W3C Recommendation](http://www.w3.org/TR/xslt#output), [Constant Field Values](../../../constant-values.md)**

    - #### **ENCODING**

          public static final java.lang.String ENCODING

      **encoding = `string`.**
      **`encoding` specifies the preferred character encoding that the Transformer should use to encode sequences of characters as sequences of bytes. The value of the attribute should be treated case-insensitively. The value must only contain characters in the range \#x21 to \#x7E (i.e., printable ASCII characters). The value should either be a `charset` registered with the Internet Assigned Numbers Authority \[IANA\], \[RFC2278\] or start with `X-`.**

      **See Also:**
      **[section 16 of the XSL Transformations (XSLT) W3C Recommendation](http://www.w3.org/TR/xslt#output), [Constant Field Values](../../../constant-values.md)**

    - #### **OMIT_XML_DECLARATION**

          public static final java.lang.String OMIT_XML_DECLARATION

      **omit-xml-declaration = "yes" \| "no".**
      **`omit-xml-declaration` specifies whether the XSLT processor should output an XML declaration; the value must be `yes` or `no`.**

      **See Also:**
      **[section 16 of the XSL Transformations (XSLT) W3C Recommendation](http://www.w3.org/TR/xslt#output), [Constant Field Values](../../../constant-values.md)**

    - #### **STANDALONE**

          public static final java.lang.String STANDALONE

      **standalone = "yes" \| "no".**
      **`standalone` specifies whether the Transformer should output a standalone document declaration; the value must be `yes` or `no`.**

      **See Also:**
      **[section 16 of the XSL Transformations (XSLT) W3C Recommendation](http://www.w3.org/TR/xslt#output), [Constant Field Values](../../../constant-values.md)**

    - #### **DOCTYPE_PUBLIC**

          public static final java.lang.String DOCTYPE_PUBLIC

      **doctype-public = `string`.**
      **See the documentation for the `DOCTYPE_SYSTEM` property for a description of what the value of the key should be.**

      **See Also:**
      **[section 16 of the XSL Transformations (XSLT) W3C Recommendation](http://www.w3.org/TR/xslt#output), [Constant Field Values](../../../constant-values.md)**

    - #### **DOCTYPE_SYSTEM**

          public static final java.lang.String DOCTYPE_SYSTEM

      **doctype-system = `string`.**
      **`doctype-public` specifies the public identifier to be used in the document type declaration.**

      **If the doctype-system property is specified, the xml output method should output a document type declaration immediately before the first element. The name following \<!DOCTYPE should be the name of the first element. If doctype-public property is also specified, then the xml output method should output PUBLIC followed by the public identifier and then the system identifier; otherwise, it should output SYSTEM followed by the system identifier. The internal subset should be empty. The doctype-public attribute should be ignored unless the doctype-system attribute is specified.**

      **If the doctype-public or doctype-system attributes are specified, then the html output method should output a document type declaration immediately before the first element. The name following \<!DOCTYPE should be HTML or html. If the doctype-public attribute is specified, then the output method should output PUBLIC followed by the specified public identifier; if the doctype-system attribute is also specified, it should also output the specified system identifier following the public identifier. If the doctype-system attribute is specified but the doctype-public attribute is not specified, then the output method should output SYSTEM followed by the specified system identifier.**

      **`doctype-system` specifies the system identifier to be used in the document type declaration.**

      **See Also:**
      **[section 16 of the XSL Transformations (XSLT) W3C Recommendation](http://www.w3.org/TR/xslt#output), [Constant Field Values](../../../constant-values.md)**

    - #### **CDATA_SECTION_ELEMENTS**

          public static final java.lang.String CDATA_SECTION_ELEMENTS

      **cdata-section-elements = `expanded names`.**
      **`cdata-section-elements` specifies a whitespace delimited list of the names of elements whose text node children should be output using CDATA sections.**

      **See Also:**
      **[section 16 of the XSL Transformations (XSLT) W3C Recommendation.](http://www.w3.org/TR/xslt#output), [Constant Field Values](../../../constant-values.md)**

    - #### **INDENT**

          public static final java.lang.String INDENT

      **indent = "yes" \| "no".**
      **`indent` specifies whether the Transformer may add additional whitespace when outputting the result tree; the value must be `yes` or `no`.**

      **See Also:**
      **[section 16 of the XSL Transformations (XSLT) W3C Recommendation](http://www.w3.org/TR/xslt#output), [Constant Field Values](../../../constant-values.md)**

    - #### **MEDIA_TYPE**

          public static final java.lang.String MEDIA_TYPE

      **media-type = `string`.**
      **`media-type` specifies the media type (MIME content type) of the data that results from outputting the result tree. The `charset` parameter should not be specified explicitly; instead, when the top-level media type is `text`, a `charset` parameter should be added according to the character encoding actually used by the output method.**

      **See Also:**
      **[section 16 of the XSL Transformations (XSLT) W3C Recommendation](http://www.w3.org/TR/xslt#output), [Constant Field Values](../../../constant-values.md)**

**Skip navigation links**

- **[Overview](../../../overview-summary.md)**
- **[Package](package-summary.md)**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../deprecated-list.md)**
- **[Index](../../../index-all.md)**
- **[Help](../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](ErrorListener.md)**
- **[Next Class](Result.md)**

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
