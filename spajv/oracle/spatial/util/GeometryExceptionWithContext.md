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

- [Prev Class](GeoHash.md)
- [Next Class](GML.md)

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

## Class GeometryExceptionWithContext

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - oracle.spatial.util.GeometryExceptionWithContext

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class GeometryExceptionWithContext
      extends java.lang.Exception

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                  |
    |------------------------------------------------------------------------------------------------------------------------------|
    | `GeometryExceptionWithContext``(java.lang.String oracleErrorMessage, java.lang.String specifics, java.lang.String context)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description       |
    |--------------------|------------------------------|
    | `java.lang.String` | `getContext``()`             |
    | `java.lang.String` | `getOracleErrorMessage``()`  |
    | `java.lang.String` | `getSpecifics``()`           |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GeometryExceptionWithContext

          public GeometryExceptionWithContext(java.lang.String oracleErrorMessage,
                                              java.lang.String specifics,
                                              java.lang.String context)

  <!-- -->

  - ### Method Detail

    - #### getOracleErrorMessage

          public java.lang.String getOracleErrorMessage()

    <!-- -->

    - #### getSpecifics

          public java.lang.String getSpecifics()

    <!-- -->

    - #### getContext

          public java.lang.String getContext()

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

- [Prev Class](GeoHash.md)
- [Next Class](GML.md)

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
