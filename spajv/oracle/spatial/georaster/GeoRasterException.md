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

- [Prev Class](GCPPoint.md)
- [Next Class](GeorColormap.md)

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

oracle.spatial.georaster

## Class GeoRasterException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - oracle.spatial.georaster.GeoRasterException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class GeoRasterException
      extends java.lang.Exception

  The class GeoRasterException is a subclass of Exception, and it indicates conditions related to JGeoRaster that an application might want to catch.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                |
    |----------------------------------------------------------------------------------------------------------------------------|
    | `GeoRasterException``(java.lang.String message)`<br>Constructs a new GeoRasterException with the specified detail message. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                                          |
    |-----------------------------|-----------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`          | `getMessage``()`<br>Returns the detailed message string of this GeoRasterException instance.                    |
    | `static GeoRasterException` | `getVersionException``(java.lang.String version)`<br>Returns a GeoRasterException instance about version issue. |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GeoRasterException

          public GeoRasterException(java.lang.String message)

      Constructs a new GeoRasterException with the specified detail message.
      Parameters:
      `message` - the detail message.

  <!-- -->

  - ### Method Detail

    - #### getMessage

          public java.lang.String getMessage()

      Returns the detailed message string of this GeoRasterException instance.
      Overrides:
      `getMessage` in class `java.lang.Throwable`

      Returns:
      the detailed message string of this GeoRasterException instance.

    <!-- -->

    - #### getVersionException

          public static GeoRasterException getVersionException(java.lang.String version)

      Returns a GeoRasterException instance about version issue.
      Returns:
      a GeoRasterException instance about version issue.

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

- [Prev Class](GCPPoint.md)
- [Next Class](GeorColormap.md)

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
