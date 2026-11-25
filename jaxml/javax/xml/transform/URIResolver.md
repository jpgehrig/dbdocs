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

- **[Prev Class](TransformerFactoryConfigurationError.md)**
- **Next Class**

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

## **Interface URIResolver**

-

  ------------------------------------------------------------------------

  **
  **

      public interface URIResolver

  **An object that implements this interface that can be called by the processor to turn a URI used in document(), xsl:import, or xsl:include into a Source object.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type     | Method and Description                                                                                                                                      |
    |-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Source`](Source.md) | `resolve``(java.lang.String href, java.lang.String base)`<br>Called by the processor when it encounters an xsl:include, xsl:import, or document() function. |

<!-- -->

- - ### Method Detail

    - #### resolve

          Source resolve(java.lang.String href,
                         java.lang.String base)
                  throws TransformerException

      Called by the processor when it encounters an xsl:include, xsl:import, or document() function.
      Parameters:
      `href` - An href attribute, which may be relative or absolute.

      `base` - The base URI in effect when the href attribute was encountered.

      Returns:
      A Source object, or null if the href cannot be resolved, and the processor should try to resolve the URI itself.

      Throws:
      [`TransformerException`](TransformerException.md) - if an error occurs when trying to resolve the URI.

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

- **[Prev Class](TransformerFactoryConfigurationError.md)**
- **Next Class**

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
