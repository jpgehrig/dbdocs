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

- [Prev Class](CompJGeom.md)
- [Next Class](DataException.md)

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

oracle.spatial.geometry

## Class CoordSysInfo

- java.lang.Object

- - oracle.spatial.geometry.CoordSysInfo

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class CoordSysInfo
      extends java.lang.Object
      implements java.io.Serializable

  Immutable, thread-safe class that stores simplified coordinate system information.
  Spherical coordinate systems return an inverse flattening of POSITIVE_INFINITY. Projected coordinate systems return NaN for semi-major axis and inverse flattening.

  This class knows the geodetic coordinate systems distributed with the Oracle database; any other SRID is treated as projected by default.

  SRID values can be customized before first use, overriding the database defaults. Once used, the definition of a SRID can not be changed.

  Since:
  12.2

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                                                                               |
    |-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static CoordSysInfo` | `createCoordSysInfo``(int srid)`<br>Define a SRID to be a projected coordinate system, overriding the default values.                                                |
    | `static CoordSysInfo` | `createCoordSysInfo``(int srid, double smax, double iflat)`<br>Define a SRID to be a geodetic coordinate system (longitude/latitude), overriding the default values. |
    | `double`              | `defaultTolerance``()`<br>Returns a suitable tolerance for use with this coordinate system.                                                                          |
    | `boolean`             | `equals``(java.lang.Object obj)`                                                                                                                                     |
    | `static CoordSysInfo` | `getCoordsys``(int srid)`<br>Return the CoordSysInfo for the given SRID.                                                                                             |
    | `int`                 | `hashCode``()`                                                                                                                                                       |
    | `double`              | `iflat``()`                                                                                                                                                          |
    | `boolean`             | `isGeodetic``()`                                                                                                                                                     |
    | `double`              | `smax``()`                                                                                                                                                           |
    | `int`                 | `srid``()`                                                                                                                                                           |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### srid

          public int srid()

    <!-- -->

    - #### isGeodetic

          public boolean isGeodetic()

    <!-- -->

    - #### smax

          public double smax()

    <!-- -->

    - #### iflat

          public double iflat()

    <!-- -->

    - #### defaultTolerance

          public double defaultTolerance()

      Returns a suitable tolerance for use with this coordinate system.
      Returns:
      an appropriate tolerance value.

    <!-- -->

    - #### createCoordSysInfo

          public static CoordSysInfo createCoordSysInfo(int srid)

      Define a SRID to be a projected coordinate system, overriding the default values. SRIDs can not be changed after definition. Definition must happen before first use of the SRID. SRID 0 can not be changed.
      Parameters:
      `srid` - SRID of projected coordinate system.

      Returns:
      the defined coordinate system (also remembered internally)

    <!-- -->

    - #### createCoordSysInfo

          public static CoordSysInfo createCoordSysInfo(int srid,
                                                        double smax,
                                                        double iflat)

      Define a SRID to be a geodetic coordinate system (longitude/latitude), overriding the default values. SRIDs can not be changed after definition. Definition must happen before first use of the SRID. SRID 0 can not be changed.
      Parameters:
      `srid` - SRID of a geodetic coordinate system.

      `smax` - semi-major axis of ellipsoid

      `iflat` - inverse flattening

      Returns:
      the defined coordinate system (also remembered inernally)

    <!-- -->

    - #### getCoordsys

          public static CoordSysInfo getCoordsys(int srid)

      Return the CoordSysInfo for the given SRID.
      Parameters:
      `srid` - the SRID to search for

      Returns:
      coordinate system information

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object obj)

      Overrides:
      `equals` in class `java.lang.Object`

    <!-- -->

    - #### hashCode

          public int hashCode()

      Overrides:
      `hashCode` in class `java.lang.Object`

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

- [Prev Class](CompJGeom.md)
- [Next Class](DataException.md)

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
