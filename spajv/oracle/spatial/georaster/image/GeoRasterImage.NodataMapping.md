Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](GeoRasterImage.md)
- [Next Class](GeoRasterImageProcessUtil.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.georaster.image

## Class GeoRasterImage.NodataMapping

- java.lang.Object

- - oracle.spatial.georaster.image.GeoRasterImage.NodataMapping

<!-- -->

- Enclosing class:
  [GeoRasterImage](GeoRasterImage.md)

  ------------------------------------------------------------------------



      public class GeoRasterImage.NodataMapping
      extends java.lang.Object

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type  | Field and Description                                                   |
    |--------------------|-------------------------------------------------------------------------|
    | `boolean`          | `m_isRange`<br>indicate if it is nodata range or nodata value           |
    | `boolean`          | `m_isTransparent`<br>set nodata pixels to transparent or opaque         |
    | `java.lang.Double` | `m_new_value`<br>new value for any pixel value in this no data range    |
    | `double`           | `m_nodata_end`<br>the lower bound of nodata range, which is exclusive   |
    | `double`           | `m_nodata_start`<br>the lower bound of nodata range, which is inclusive |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                   |
    |---------------------------------------------------------------------------------------------------------------|
    | `NodataMapping``(double nodata_start, java.lang.Double new_value, boolean isTransparent)`                     |
    | `NodataMapping``(double nodata_start, double nodata_end, java.lang.Double new_value, boolean isTransparent)`  |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### m_nodata_start

          public double m_nodata_start

      the lower bound of nodata range, which is inclusive

    <!-- -->

    - #### m_nodata_end

          public double m_nodata_end

      the lower bound of nodata range, which is exclusive

    <!-- -->

    - #### m_new_value

          public java.lang.Double m_new_value

      new value for any pixel value in this no data range

    <!-- -->

    - #### m_isTransparent

          public boolean m_isTransparent

      set nodata pixels to transparent or opaque

    <!-- -->

    - #### m_isRange

          public boolean m_isRange

      indicate if it is nodata range or nodata value

  <!-- -->

  - ### Constructor Detail

    - #### NodataMapping

          public NodataMapping(double nodata_start,
                               double nodata_end,
                               java.lang.Double new_value,
                               boolean isTransparent)

    <!-- -->

    - #### NodataMapping

          public NodataMapping(double nodata_start,
                               java.lang.Double new_value,
                               boolean isTransparent)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](GeoRasterImage.md)
- [Next Class](GeoRasterImageProcessUtil.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
