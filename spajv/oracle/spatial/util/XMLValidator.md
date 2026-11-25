Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](WKT.md)
- [Next Class](XMLValidator2.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.spatial.util

## Class XMLValidator

- java.lang.Object

- - oracle.spatial.util.XMLValidator

<!-- -->

-

  ------------------------------------------------------------------------



      public class XMLValidator
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `XMLValidator``()`          |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                       |
    |-------------------|------------------------------------------------------------------------------|
    | `static void`     | `main``(java.lang.String[] args)`                                            |
    | `static void`     | `process``(java.lang.String xmlfile, java.lang.String xsdfile)`              |
    | `static void`     | `processValidateXML``(java.lang.String xmlURI, java.lang.Object schemadoc)`  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XMLValidator

          public XMLValidator()

  <!-- -->

  - ### Method Detail

    - #### process

          public static void process(java.lang.String xmlfile,
                                     java.lang.String xsdfile)
                              throws java.lang.Exception

      Parameters:
      `xmlfile` - The file name for the XML file to be validated.

      `xsdfile` - The file name for the XSD file to be validated. All dependent XSDs must be included in the parent file.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### processValidateXML

          public static void processValidateXML(java.lang.String xmlURI,
                                                java.lang.Object schemadoc)
                                         throws java.lang.Exception

      Parameters:
      `xmlURI` - The URI String for the XML file to be validated.

      `schemadoc` - The schema document Object for the XSD file to be validated.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### main

          public static void main(java.lang.String[] args)
                           throws java.lang.Exception

      Throws:
      `java.lang.Exception`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](WKT.md)
- [Next Class](XMLValidator2.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
