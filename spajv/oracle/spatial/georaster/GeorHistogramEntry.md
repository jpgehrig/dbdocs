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

- [Prev Class](GeorHistogram.md)
- [Next Class](GeorSpatialReference.md)

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

## Class GeorHistogramEntry

- java.lang.Object

- - oracle.spatial.georaster.GeorHistogramEntry

<!-- -->

-

  ------------------------------------------------------------------------



      public class GeorHistogramEntry
      extends java.lang.Object

  A GeoRaster grayscale entry, which contains two components: value and count. It is combined with class GeorHistogram to represent a GeoRaster histogram.
  Two constructors are provided: one is the default constructor without parameters, and the other constructor allows you to specify cell value and count value.

  Methods in this class are provided for retrieving and setting the cell value and count.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                            |
    |----------------------------------------------------------------------------------------------------------------------------------------|
    | `GeorHistogramEntry``()`<br>Constructs a `GeorGrayscaleEntry` object.                                                                  |
    | `GeorHistogramEntry``(double value, long count)`<br>Constructs a `GeorHistogramEntry` object with the given cell value and gray value. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                             |
    |-------------------|----------------------------------------------------|
    | `double`          | `getCellValue``()`<br>Returns the cell value.      |
    | `long`            | `getCount``()`<br>Returns the count value.         |
    | `void`            | `setCount``(long count)`<br>Sets the count value.  |
    | `void`            | `setValue``(double value)`<br>Sets the cell value. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GeorHistogramEntry

          public GeorHistogramEntry()

      Constructs a `GeorGrayscaleEntry` object.

    <!-- -->

    - #### GeorHistogramEntry

          public GeorHistogramEntry(double value,
                                    long count)

      Constructs a `GeorHistogramEntry` object with the given cell value and gray value.
      Parameters:
      `value` - cell value

      `count` - count value

  <!-- -->

  - ### Method Detail

    - #### getCellValue

          public double getCellValue()

      Returns the cell value.
      Returns:
      cell value

    <!-- -->

    - #### setValue

          public void setValue(double value)

      Sets the cell value.
      Parameters:
      `value` - cell value

    <!-- -->

    - #### getCount

          public long getCount()

      Returns the count value.
      Returns:
      count value

    <!-- -->

    - #### setCount

          public void setCount(long count)

      Sets the count value.
      Parameters:
      `count` - count value

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

- [Prev Class](GeorHistogram.md)
- [Next Class](GeorSpatialReference.md)

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
