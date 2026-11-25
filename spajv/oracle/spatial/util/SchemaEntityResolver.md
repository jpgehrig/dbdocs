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

- [Prev Class](SampleShapefileToJGeomFeature.md)
- [Next Class](SDODoubleGeneralPath.md)

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

## Class SchemaEntityResolver

- java.lang.Object

- - oracle.spatial.util.SchemaEntityResolver

<!-- -->

- All Implemented Interfaces:
  org.xml.sax.EntityResolver

  ------------------------------------------------------------------------



      public class SchemaEntityResolver
      extends java.lang.Object
      implements org.xml.sax.EntityResolver

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                        |
    |----------------------------------------------------|
    | `SchemaEntityResolver``(java.sql.Connection cnn)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type         | Method and Description                                                   |
    |---------------------------|--------------------------------------------------------------------------|
    | `org.xml.sax.InputSource` | `resolveEntity``(java.lang.String targetNS, java.lang.String systemId)`  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SchemaEntityResolver

          public SchemaEntityResolver(java.sql.Connection cnn)

  <!-- -->

  - ### Method Detail

    - #### resolveEntity

          public org.xml.sax.InputSource resolveEntity(java.lang.String targetNS,
                                                       java.lang.String systemId)
                                                throws org.xml.sax.SAXException,
                                                       java.io.IOException,
                                                       java.lang.RuntimeException

      Specified by:
      `resolveEntity` in interface `org.xml.sax.EntityResolver`

      Parameters:
      `targetNS` - Namespace

      `systemId` - URL

      Returns:
      Throws:
      `org.xml.sax.SAXException`

      `java.io.IOException`

      `java.lang.RuntimeException`

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

- [Prev Class](SampleShapefileToJGeomFeature.md)
- [Next Class](SDODoubleGeneralPath.md)

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
