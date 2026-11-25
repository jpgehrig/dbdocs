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

- **[Prev Class](SourceLocator.md)**
- **[Next Class](Transformer.md)**

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

## **Interface Templates**

- **All Known Implementing Classes:**
  **[XSLStylesheet](../../../oracle/xml/parser/v2/XSLStylesheet.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Templates

  **An object that implements this interface is the runtime representation of processed transformation instructions.**
  **Templates must be threadsafe for a given instance over multiple threads running concurrently, and may be used multiple times in a given session.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type               | Method and Description                                                                 |
    |---------------------------------|----------------------------------------------------------------------------------------|
    | `java.util.Properties`          | `getOutputProperties``()`<br>Get the static properties for xsl:output.                 |
    | [`Transformer`](Transformer.md) | `newTransformer``()`<br>Create a new transformation context for this Templates object. |

<!-- -->

- - ### Method Detail

    - #### newTransformer

          Transformer newTransformer()
                              throws TransformerConfigurationException

      Create a new transformation context for this Templates object.
      Returns:
      A valid non-null instance of a Transformer.

      Throws:
      [`TransformerConfigurationException`](TransformerConfigurationException.md) - if a Transformer can not be created.

    <!-- -->

    - #### getOutputProperties

          java.util.Properties getOutputProperties()

      Get the static properties for xsl:output. The object returned will be a clone of the internal values. Accordingly, it can be mutated without mutating the Templates object, and then handed in to [`Transformer.setOutputProperties(java.util.Properties)`](Transformer.md).
      The properties returned should contain properties set by the stylesheet, and these properties are "defaulted" by default properties specified by [section 16 of the XSL Transformations (XSLT) W3C Recommendation](http://www.w3.org/TR/xslt#output). The properties that were specifically set by the stylesheet should be in the base Properties list, while the XSLT default properties that were not specifically set should be in the "default" Properties list. Thus, getOutputProperties().getProperty(String key) will obtain any property in that was set by the stylesheet, *or* the default properties, while getOutputProperties().get(String key) will only retrieve properties that were explicitly set in the stylesheet.

      For XSLT, [Attribute Value Templates](http://www.w3.org/TR/xslt#attribute_value_templates) attribute values will be returned unexpanded (since there is no context at this point). The namespace prefixes inside Attribute Value Templates will be unexpanded, so that they remain valid XPath values. (For XSLT 1.0, this is not a problem since Attribute Value Templates are not allowed for xsl:output attributes. However, the will be allowed in versions after 1.1.)

      Returns:
      A Properties object, never null.

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

- **[Prev Class](SourceLocator.md)**
- **[Next Class](Transformer.md)**

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
